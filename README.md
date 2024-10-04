# xAPI Prepositions

## What is it?

xAPI Prepositions provides a means of adding prepositional relationships between actors and objects with xAPI. Leveraging context extensions, xAPI Prepositions provides 150 English-language prepositions ready for use in xAPI statements. Note that these extensions are designed as prepositions -- not as adverbs. So: "actor placed the bread on/under/beside the counter" not "actor turned the light on".

This takes the form of a JSON-LD xAPI Profile containing individual Preposition concepts.

## Example Usage

You can use xAPI Prepositions for many situations in xAPI where you have an indirect object.

For a simple example, consider the common system feature of login impersonation. An admin user logs into a system (LMS for example) AS another user. We would want to know both who they were, what they did, and who they did it "as". That might look like the following:

```
{
    "actor": {
        "name": "Joe Instructor",
        "account": {
            "homePage": "https://lms.example/id",
            "name": "048863bf-34ee-4c5f-a0e4-94f67ee1fb93"
        }
    },
    "verb": {
        "id": "https://lms.example/profile/concepts/verbs/login",
        "display": {
            "en": "Logged In"
        }
    },
    "object": {
        "id": "https://lms.example/",
        "definition": {
            "type": "https://lms.example/profile/activitytype/lms",
            "name": {
                "en-US": "Example LMS"
            }
        }
    },
    "result": {
        "success": true
    },
    "context": {
        "extensions": {
            "https://yetanalytics.com/profiles/prepositions/concepts/context-extensions/as": {
                "name": "Jill Learner",
                "account": {
                    "homePage": "https://lms.example/id",
                    "name": "048863bf-34ee-4c5f-a0e4-94f67ee1fb92"
                }
            }
        }
    }
}

```

The result is a statement that says, if you were to read it as a sentence:

`Joe Instructor logs into the LMS "as" Jill Learner`


## License

Copyright © 2021-2024 Yet Analytics, Inc.

Distributed under the Apache License version 2.0.
