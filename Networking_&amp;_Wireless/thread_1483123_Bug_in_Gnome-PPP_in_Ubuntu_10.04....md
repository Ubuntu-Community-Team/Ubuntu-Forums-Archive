---
title: "Bug in Gnome-PPP in Ubuntu 10.04..."
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by pradeepthundiyil on 2010-05-14
hi,

To all those who have problems with connecting datacard.. I had issues in connecting my datacard. I could solve it through the suggestions in forum.. I dont use Windows anymore.. I love ubuntu..

Follow the steps and reboot..


The on going saga of the Network Manager failing to return the NS1 and NS2
IE the modem connects but the Browser and updates etc fail to connect

Here I have change the IPCP configure-NAKs returned before starting , remove the # and set the number to 30 ( or any thing above the default value till there is a constant connection )

Code:

sudo gedit /etc/ppp/options

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
ipcp-max-failure 30

Hopefully I can now leave the NM IPv4 settings to Automatic (PPP) instead of Setting the NM to IPv4 settings to Automatic (PPP) address only and having to enter the numerical addresses in the DNS servers text box.

I will be monitoring the outcome of this change.


Also try this from a recent post / but also has roots from the past / please read the thread


[http://ubuntuforums.org/showthread.php?t=1426409](http://ubuntuforums.org/showthread.php?t=1426409)




Code:
gksudo gedit /etc/ppp/options
Add this line and save:

replacedefaultroute

if this is done then replace the # in front of the

replace the # in front of the " ipcp-max-failure 30 " do not use both lines


also the replacedefaulte has failed a few times after a fresh boot , but has proved quite successful


#reboot

---

### Post by pdc on 2010-05-14
> **Kindly provide some suggestions.. Thank you**..

upgrade may imply some sort of improvement to many; perhaps "change" would be a better way to describe changing from one version to another;

each new version carries problems; 

if connecting to the internet is key, folks may be better reinstalling what they know worked;if the new does not work;

and each time they think of **exploring** a new release, perhaps best to download the iso; create a mobile USB stick version;  (from the handy utility in ubuntu); and check if it works before committing to the new; (or just create a small partition to add the new version into ..........)

---

### Post by alexfish on 2010-05-14
hi

to say one thing and mean another is like saying you have a problem

Gnomeppp is only the dialer , the title of your thread is inappropriate

if you wish to report bugs there may be help here

 [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

regards

alexfish

---

