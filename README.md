# ocp_add_user_to_tenancy

## Description:

This role adds a list of users to an existing tenancy.

## Behaviour:

**Feature:** Add users to a tenancy

As a PaaS Operator
I want to add a list of users to an existing tenancy
so that the users can work on projects in the tenancy

- **Scenario:** A customer requests new users
- **Given:** there is a valid service account token
- **Given:** there is an existing tenancy
- **Given:** there is a list of users
- **When:** the role is executed
- **Then:** the users are added to the tenancy 
 
## Configuration:

A list of the external variables used by the role.

| Variable  | Description  | Example  | Default |
|---|---|---|---|
| **tenancy**  | The name of the tenancy |  mytenancy | (none) |
| **users**  | List of users to add to the tenancy | alice,bob,charlie  |  (none) |
| **ocp_token**  | Token for a serviceaccount with permission to create projects | (none)  |
| **ocp_uri**  | URI for the cluster API | https://localhost:8443/  |

## Testing and Usage:

The role can be tested using a simple playbook as follows:

```
---

- hosts: masters[0]
  name: Testing ocp_create_tenancy
  roles:
    - ocp_add_user_to_tenancy
  vars:
    - tenancy: mytenancy
    - users:
      - alice
      - bob
      - charlie
    - ocp_token: eyJhb...

```
