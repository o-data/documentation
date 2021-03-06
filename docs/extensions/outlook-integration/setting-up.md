# Outlook Integration. Setting-up for Administrator

* [Integration](#integration)
* [Access control](#access-control)
* [Sync scheduling](#sync-scheduling)
* [Troubleshooting](#troubleshooting)

## Integration

Go to the Administration > Integrations > Outlook. Check *Enabled* checkbox.

* *Client ID* and *Client Secret* you will obtain in Azure Active Directory admin center.
* *Redirect URI* you will need to copy to Azure Active Directory admin center.

![Integration](../../_static/images/extensions/outlook-integration/setting-up/1.png)

**1\.** Go to [aad.portal.azure.com](https://aad.portal.azure.com).

**2\.** Create an application.

Follow Azure Active Directory > App registration > Register an application.

![App registration](../../_static/images/extensions/outlook-integration/setting-up/2.png)

Select needed *Supported account types*.

Copy *Redirect URI* from EspoCRM. Note, that type should be set to `Web`.

![App registration](../../_static/images/extensions/outlook-integration/setting-up/3.png)

**3\.** Copy *Application (client) ID* from Azure app to EspoCRM.

![Client ID](../../_static/images/extensions/outlook-integration/setting-up/4.png)

![Client ID](../../_static/images/extensions/outlook-integration/setting-up/5.png)

**4\.** Create a secret for Azure app. Copy it to EspoCRM.

![Secret](../../_static/images/extensions/outlook-integration/setting-up/6.png)

![Secret](../../_static/images/extensions/outlook-integration/setting-up/7.png)

![Secret](../../_static/images/extensions/outlook-integration/setting-up/8.png)

![Secret](../../_static/images/extensions/outlook-integration/setting-up/9.png)

**5\.** Save Outlook integration credentials in EspoCRM.

**6\.** Grant required permissions for Azure app.

Note: This step is required for Office365 users. For Outlook it usually works with out this step, but it might be needed either.

Click *Api Permissions* on the left panel. Click *Add a permission*. Click *Microsoft Graph*. Click *Delegated permissions*. Then use search to find needed permissions and enable them.

Permissions that are needed to be enabled:

* offline_access – mandatory
* Calendars.ReadWrite – optional – for calendar sync
* Contacts.ReadWrite – optional – for contacts pushing
* IMAP.AccessAsUser.All – optional – for email fetching
* SMTP.Send – optional – for email sending

![Permissions](../../_static/images/extensions/outlook-integration/setting-up/10.png)


## Access control

**Important**: By default regular users don’t have access to Outlook Calendar integration. Administrator needs to enable access in Roles. The following scopes need to be enabled:

* External Accounts
* Outlook Calendar
* Outlook Contacts

![Roles](../../_static/images/extensions/outlook-integration/setting-up/roles.png)


## Sync scheduling

Sync is run by the scheduled job *Outlook Calendar Sync*. By default it executes every 10 minutes. You can change a scheduling at Administration > Scheduled Jobs > Outlook Calendar Sync.

## Troubleshooting

Check whether the scheduled job is running Administration > Scheduled Jobs > Outlook Calendar Sync > Log.

Check EspoCRM log at `data/logs` directory. You can also set the [log mode](../../administration/troubleshooting.md#enabling-debug-mode-for-a-logger) to `DEBUG` level to obtain more info from the log.