The release.yml and release-dev.yml workflows draft and package releases for the master and development branches respectively:

- Drafts a release every time something is pushed to the master or dev branches. Release drafter uses pull requests to create the changelog and is customized via the release-drafter.yml config files in the directory above and via the issue tags in the repo.
- Builds an exist package with ant and attaches it to the release.
    - NOTE: The version must match the version number in /expath-pkg.xml otherwise the workflow will fail! In other words, you should predict the next version number (semantic versioning) to be used by release drafter, and make sure this is included in expath-pkg.xml at the time of the push.
- Loads the exist package into a docker image (into which the data from the usaybia-data repo has already been loaded via the workflow in that repo) and posts it to the GitHub container repository.