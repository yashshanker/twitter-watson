# Personality Insights Python Starter Application

  The IBM Watson [Personality Insights][service_url] service uses linguistic analysis to extract cognitive and social characteristics from input text such as email, text messages, tweets, forum posts, and more. By deriving cognitive and social preferences, the service helps users to understand, connect to, and communicate with other people on a more personalized level.

Give it a try! Click the button below to fork into IBM DevOps Services and deploy your own copy of this application on Bluemix.

[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/watson-developer-cloud/personality-insights-python)

## Getting Started

1. Create a Bluemix Account

    [Sign up][sign_up] in Bluemix, or use an existing account. Watson Services in Beta are free to use.

2. Download and install the [Cloud-foundry CLI][cloud_foundry] tool

3. Edit the `manifest.yml` file and change the `<application-name>` to something unique.
  ```none
  applications:
  - name: personality-insights-python
    command: python server.py
    path: .
    memory: 256M
    services:
    - personality-insights-service
  ```

    The name you use will determinate your application url initially, e.g. `<application-name>.mybluemix.net`.

4. Connect to Bluemix in the command line tool
  ```sh
  $ cf api https://api.ng.bluemix.net
  $ cf login -u <your user ID>
  ```

5. Create the Personality Insights service in Bluemix

  ```sh
  $ cf create-service personality_insights tiered personality-insights-service
  ```

6. Push it live!

  ```sh
  $ cf push
  ```

  See the full [Getting Started][getting_started] documentation for more details, including code snippets and references.

## Running locally
  The application uses [Python](https://www.python.org) and [pip](https://pip.pypa.io/en/latest/installing.html) so you will have to download and install them as part of the steps below.

1. Copy the credentials from your `personality-insights-service` service in Bluemix to `server.py`, you can see the credentials using:

  ```sh
  $ cf env <application-name>
  ```
  Example output:
  ```sh
  System-Provided:
  {
  "VCAP_SERVICES": {
    "personality_insights": [{
        "credentials": {
          "url": "<url>",
          "password": "<password>",
          "username": "<username>"
        },
      "label": "personality_insights",
      "name": "personality-insights-service",
      "plan": "IBM Watson Personality Insights Monthly Plan"
   }]
  }
  }
  ```

    You need to copy `username`, `password` and `url`.

2. Install [Python 2.7.9 or later](https://www.python.org/downloads/)
3. Go to the project folder in a terminal and run:
  `pip install -r requirements.txt`
4. Start the application
  `python server.py`
5. Go to
  `http://localhost:3000`


## Troubleshooting

To troubleshoot your Bluemix app the main useful source of information are the logs, to see them, run:

  ```sh
  $ cf logs <application-name> --recent
  ```

## License

  This sample code is licensed under Apache 2.0. Full license text is available in [LICENSE](LICENSE).

## Contributing

  See [CONTRIBUTING](CONTRIBUTING.md).

## Open Source @ IBM
  Find more open source projects on the [IBM Github Page](http://ibm.github.io/)

[service_url]: http://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/personality-insights.html
[cloud_foundry]: https://github.com/cloudfoundry/cli
[getting_started]: https://www.ibm.com/watson/developercloud/doc/common/
[sign_up]: https://apps.admin.ibmcloud.com/manage/trial/bluemix.html?cm_mmc=WatsonDeveloperCloud-_-LandingSiteGetStarted-_-x-_-CreateAnAccountOnBluemixCLI
