---
title: "use of mythfilldatabase in 8.10"
date: 2009-03-01
forum: Mythbuntu
---

### Post by neutron68 on 2009-03-01
I'm trying to force the mythfilldatabase command to run, in a terminal window - in order to fill out my program schedule following a rescan of digital tv channels.

Should the command be used with a sudo (as root) or without (as a regular user)?

I've been using "sudo mythfilldatabase --refresh-all" and the process only lasts for about 10 seconds - rather than the 5 minutes it SHOULD last.  I know the process didn't run properly because the program guide data still has NO DATA for the newly scanned digital channels.

-edit-

I have now tried it both ways - with a sudo and without.  Neither way works.
I know there was tv guide data for the first 2 weeks of the operation of Mythbuntu...now the channel data bars all say NO DATA.  The Mythbuntu box was in DHCP mode when it was first loaded and pulled down the guide data.  
Later, I set the Mythbuntu box to a static IP address.  Due to the bugs in the Network Manager application, I had to use the file editing method to set a static IP.
I used this page as my guide [http://dev-notes.com/code.php?q=26](http://dev-notes.com/code.php?q=26)

Now, I'm testing the Internet access of the Mythbuntu box using Firefox.  
I can't get to sites by their URLs, but can get to sites by their IP addresses.  

I guess I have a DNS setting problem?

-edit-

That was it - a DNS problem.

I just performed the following and mythfilldatabase works now:

> 1.  sudo nano /etc/resolv.conf

2.  added this nameserver line:
nameserver <ip address of my router>

3.  saved the file
4.  sudo /etc/init.d/networking restart

Eric

---

### Post by klc5555 on 2009-03-01
> **neutron68 said:**
> I'm trying to force the mythfilldatabase command to run, in a terminal window - in order to fill out my program schedule following a rescan of digital tv channels.

Should the command be used with a sudo (as root) or without (as a regular user)?

I've been using "sudo mythfilldatabase --refresh-all" and the process only lasts for about 10 seconds - rather than the 5 minutes it SHOULD last.  I know the process didn't run properly because the program guide data still has NO DATA for the newly scanned digital channels.

-edit-

I have now tried it both ways - with a sudo and without.  Neither way works.
I know there was tv guide data for the first 2 weeks of the operation of Mythbuntu...now the channel data bars all say NO DATA.  The box was in DHCP mode when it was first loaded and pulled down the guide data.  Later, I set the Mythbuntu box to a static IP address by the file editing method.
(with sudo nano /etc/network/interfaces file)

Now, I'm testing the Internet access of the Mythbuntu box using Firefox.  I can't get to sites by their URLs, but can get to sites by their IP addresses.  

I wonder if I have a DNS setting problem?

Eric

Sounds like you're not accessing a working DNS server. You can confirm that dns is not functioning from a terminal, by querying some favorite site, e.g.: nslookup mythtv.org   If nslookup returns an ip address, it will tell you, and tell you the nameserver it found it from. If there's a problem, it will tell you that. I assume it will tell you that your default nameserver is inaccessible or invalid. 

Now usually you'd do your dhcp>static ip switchover from the desktop using Ubuntu's (admittedly pain-in-the-butt) network administration tool. Including setting in the dns server(s). 


But since you're file editing, you need to check /etc/resolv.conf to make sure that you've got a good dns server address in the first position. Edit  one in if there's none there. Each line in the resolv.conf will look something like this:

nameserver 68.87.96.3

which happens to be one of Comcast's current nameservers; you put in one for a nameserver on your local provider's network. (Or two, or three ... one nameserver per line).

Once you have a working nameserver in this file, you should have no additional difficulty getting address information.

Mythfilldatabase will be run as a regular user. sudo is not necessary. If you run mythfilldatabase --refresh-all, the data should start populating tables "tomorrow". If you want data for "today", you will have to explicitly specify "--refresh-today" in addition to whatever other parameter you specify.

If your nslookup is working, you have run mythfilldatabase apparently successfully, but you still have no data filling in, the culprit is likely that mythfilldatabase is unable to pull down the XMLTVID numbers for your channels. You will then have to put these in manually, either from the front-end by watching some channel in live tv, accessing the edit menu with the "e" keyboard shortcut and putting the xmltvid for the channel in the correct space, and then proceeding to the next channel; or from the "channel editor" in the back-end setup, by opening the specifications page for each channel and typing the xmltvid number in the correct box. 

(If you don't know where to get the xmltvid numbers for your channels, they can be got by logging into SchedulesDirect, indicating that you want to add a new lineup for your zipcode --but then instead of adding any new lineup, click  the "Preview lineup" button for the lineup you currently have. This will give you the complete list of channels, xmltvids, and call signs.)

Once the id's have been added for all the channels that need them, rerunning mythfilldatabase will cause the tables to be populated with data.

---

