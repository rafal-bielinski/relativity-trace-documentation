---
layout: default
title: ICE Chat
nav_exclude: true
---

# ICE Chat
{: .no_toc }

Collect ICE Chat messages via Relativity Collect.
{: .fs-6 .fw-300 }

1. TOC
{:toc}

---

## Overview

Deployment option B, depicted below, is required to use this data source.

![](media/ICE Chat_viaCollect/ICE_DeploymtB_Diagrm.png)

## Activities Captured

The following activities are captured:

- Room ID
- Start Time
- Message content
- Participants
- Participant Entered & Left
- Message date
- Disclaimers

## Metadata

In addition to standard metadata populated during extracting data, the O365 Teams Data Source captures the following ones:

- **DATE** - start date of a chat or start date of a slice in the chat split into slices.
- **SUBJECT** - friendly name of the team and channel.
- **FROM** - the first person to send a message in that respective slice.
- **TO** - chat attendees.
- **CONVERSATION-ID** - the unique identifier. When creating a Data Mapping, set “Read From Other Metadata Column” to **Yes**.
- **X-RSMF-EndDate** - end date of the chat / slice. When creating a Data Mapping, set “Read From Other Metadata Column” to **Yes**.
- **X-RSMF-MessageCount** - number of messages in the chat / slice. When creating a Data Mapping, set “Read From Other Metadata Column” to **Yes**.
- **X-RSMF-AttachmentCount** – number of attachments in the chat / slice. When creating a Data Mapping, set “Read From Other Metadata Column” to **Yes**.

## Document View

ICE Chat messages are captured as RMFS (Relativity Short Message Format) files. Relativity has created a Viewer experience to help reviewing RSMF data. See [Relativity Short Message Format](https://help.relativity.com/RelativityOne/Content/System_Guides/Relativity_Short_Message_Format/Relativity_Short_Message_Format.htm) for more details.

![](media/ICE Chat_viaCollect/ICE_DocumtView.png)

## Data Filtering

There are two levels of filtering data:

- **Data Source** - Data is being filtered according to specified Monitored Individuals (MI). No filter is applied at the message level. So, if MI exists in a channel, we will ingest the whole conversation for a given slice. If the conversation does not have any MIs in participants for that day, we do not ingest conversation at all.
- **Data Batch** - Only messages with data for the date that matches Data Batch collection period will be captured. For example, a message that has been exported for 10/1/2021 will be captured by the Data Batch that has collection period from “10/1/2021 00:00” to “10/2/2021 00:00”.

## Configuring Collect

Collect is used for data retrieval. Make sure Collect is installed in the workspace before configuring the data source. For detailed installation steps, see Installing Collect.

## Configuring ICE Chat Trace Data Source 

Obtain the following information about the ICE Chat SFTP server:
- Host name.
- Path.
- TCP Port.
- Username and password.

 Most parameters work the same for all Collect Data Sources. Follow the instructions from [Common Collect Data Source Functionality](#_Common_Collect_Data) section.

Below are specific parameters for ICE Chat:

In **General** section, select **ICE Chat** for the **Data Source Type**.
![](media/ICE_Chat_viaCollect/General_ICE_DataSourceType.png)

In **Settings** section, do the following:

1. **Username** - enter the SFTP username.
2. **Password** - enter the SFTP password.
6. **Host** - enter the SFTP location.
7. **Path** - enter the folder path on the SFTP.
8. **Port** - the TCP port number. Default value is 22.

![](media/ICE_Chat_viaCollect/ICE_CredentialsTab.png)

In **Advanced Configuration** section, do the following. For more information, see [Common Collect Data Source Functionality](#_Common_Collect_Data):

1. **Frequency in Minutes** - enter 1440.
2. **Merge Batches During Cold Start**: enter True.
3. **Max Number of Batches To Merge** - enter 1.
4. **Collection Period Offset in Minutes** - enter 1440.