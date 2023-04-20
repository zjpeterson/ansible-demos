# Network infrastructure as code using `network.base`

## Setup
1. Create a new "Ansible Automation Platform 2 Networking Automation Workshop"
2. Create a new "AWS Blank Open Environment"
3. Use the auto-assignment website from the Networking Workshop to get a lab seat; note the password it gives you
4. Log into the VSCode server from the Networking Workshop and open a terminal
5. Clone this repository and `cd` to it
6. Export `AWS_ACCESS_KEY_ID` and `AWS_ACCESS_KEY_ID` from the blank AWS environment in your terminal
7. In your VSCode, in your repo clone, make a `controller_password.txt` at the project root and replace the contents with the passowrd from step 3. This will be your `root` password for accessing Gitlab and it will also be your Personal Access Token for repo operations and API access.
8. Provision Gitlab in AWS `ansible-navigator run common/playbook_aws_gitlab.yml -m stdout --penv AWS_ACCESS_KEY_ID --penv AWS_ACCESS_KEY_ID` (look for a password prompt part of the way through)
9. Log into the provisioned Gitlab instance with username `root` and the password from the previous step
10. Create a new blank Gitlab project (really blank - uncheck the "Initialize repositoty with a README" option) and note the HTTPS clone address somewhere.
11. In your VSCode, in your repo clone, add a new remote using your PAT and blank repo with a command like: `git remote add gitlab https://oauth2:controllerpassword@ec2-whatever.amazonaws.com/gitlab-instance-asdf/your-repo.git`
12. Sync the existing repo content into the new remote: `git push gitlab main` - from this point forward you will make modifications in Gitlab and will have to specify this remote when running push commands
13. In your VSCode, in your repo clone, open `network_base/vars_controller.yml` and fill in the missing parts noted by `GITLAB_URL_HERE` (the base URL of your gitlab instance) and `GITLAB_REPO_HERE` (same Git URL as you used to make the new remote in step 11).
14. Configure the Controller `ansible-navigator run common/playbook_controller.yml -m stdout -e demo_name=network_base`

## Demo

coming Soon (tm)
