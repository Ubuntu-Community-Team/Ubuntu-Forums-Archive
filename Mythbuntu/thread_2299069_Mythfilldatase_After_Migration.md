---
title: "Mythfilldatase After Migration"
date: 2015-10-15
forum: Mythbuntu
---

### Post by jtpiano2 on 2015-10-15
I recently migrated my Mythbuntu system from ver 12 to ver 14.  (This is my first migration, I had always built new stand-alone systems in the past.)   I backed up my database and transferred the recordings to the new server.   When I restored the database it all seemed to go smoothly.   I also ran through the process to update the schema.  I did notice some issues with hostname and dhcp/dns.   My home router is doing dhcp based on MAC addresses.   Also, I could see in the new system that hostname was different from the DNS name provided by the router (which I did fix).      Also, I went from a physical to virtual machine which would account for the hostname/dns/dhcp issues.   Backend setup seemed to go pretty well and I *think* I have it done correctly though it's also possible I have some issues there.   So....after all this I am having trouble with mythfilldatabase.   I am getting the message "Mythfilldatabase ran but did not insert any  new data.  This could indicate a problem with..." blah blah.   I am presuming I must still have a mismatch somewhere.   I ran mythfill and grabbed a log, one area stood out to me.   Could this be the source of my problem?  

2015-10-14 22:20:14.836822 N [2472/2472] CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) - Empty LocalHostName.
2015-10-14  22:20:14.836844 I [2472/2472] CoreContext mythcontext.cpp:512  (LoadDatabaseSettings) - Using localhost value of mythbuntu
2015-10-14  22:20:14.837039 I [2472/2472] CoreContext mythcontext.cpp:693  (TestDBconnection) - Testing network connectivity to 'mythbuntube'

I am manually inserting xml data from my file and bypassing the grabber with some command line.   I did confirm that my xml file has program data.   I am using channel mapping to match up my xml guide data with the channels.   I also confirmed my source id matches my inputs and channels in the guide data.

Thoughts?  Many thanks in advance!

---

### Post by jtpiano2 on 2015-10-19
So I did some more troubleshooting over the weekend.  I built an identical vm and turned off the original.  I tried to import my xml data.  The very first time I tried to import the xml file mythweb reports that the import was successful. (the mythfill process seemed to repoort the same success)  However, when I look at the guide data it is empty.  

As a side note-I did fix the logging issue I noted above.  The TestDBConnection line now shows that it is successful in connecting to the server. (instead of testing connectivity to xxxx....)

I also scheduled a crontab -e job.  The job ran at the scheduled time but I still get the message about not inserting any new data.  (though that could be a timing issue if there is no new data between Sunday 4 PM when I ran mythfill manually and Monday 1 AM when mythfill ran automated)

---

