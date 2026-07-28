This creates a CSV file to export to TeSS software, using the
[youtube_to_csv](https://github.com/ualberta-rcg/youtube_to_csv) python code
and a Github action.

The ingredients:

* The `config.yml` has the configuration for generating the CSV file. Specifically:
  * it has a URL to a Youtube RSS feed for our channel.
  * it has some some default metadata values for each videos
  * it also has some specific metadata values for each video (identified by title)
* It has an action that then generates and commits the `youtube.csv` file on each commit.
  This action is `.github/workflows/generate_csv.yml`. The software that generates the CSV
  file is [youtube_to_csv](https://github.com/ualberta-rcg/youtube_to_csv), which the action
  checks out of Github and runs when a commit is pushed to `main` branch

The output: `youtube.csv`, which can be pointed at through a `Material CSV` source in TeSS.

TODO: maybe make the action smart enough that it only runs on changes to `config.yml`.