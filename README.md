# Gitlab to Gitea migration script.

This script uses the Gitlab and Gitea API's to migrate all data from
Gitlab to Gitea.

This script support migrating the following data:
 - Repositories & Wiki (fork status is lost)
 - Milestones
 - Labels
 - Issues (no comments)
 - Users (no profile pictures)
 - Groups (gitea中没有二级组织，因此，导入的时候，会把二级组织合并为一级组织，如：aa/bb ==> aa_bb)
 - Public SSH keys

Repositories导入时，可设置UPDATE_PROJECT=True,删除旧的。默认UPDATE_PROJECT=False

Tested with Gitlab Version 13.0.6-ce and Gitea Version 1.15.0.

## Usage
Change items in the config section of the script.

Install all dependencies via `python -m pip install -r requirements.txt` and
use python3 to execute the script.

### How to use with venv
To keep your local system clean, it might be helpful to store all Python dependencies in one folder.
Python provides a virtual environment package which can be used to accomplish this task.

```bash
python3 -m venv migration-env
source migration-env/bin/activate
python3 -m pip install -r requirements.txt
```

Then start the migration script `python3 migrate.py`.