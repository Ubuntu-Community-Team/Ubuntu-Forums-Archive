---
title: "Sudden loss of wireless networking."
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by faust99 on 2010-03-16
For most of today I had my internet connection dropping out on me intermittently. I assumed it was a provider issue, as it has been unreliable in the past. 

After it dropped out for good, and I could not print through network, I realised it was not a provider issue. All the other computers in the house were connected, including another ubuntu box. Only the MacBook Pro 5,5 was not able to connect.

The network manager indicated I was connected to the network, throughout the whole time. 

A number of restarts with the kernel I normally use (2.6.31-19) including one in recovery mode, yielded no change, but a restart with the 2.6.31-20 kernel resulted in connectivity.

Finally, perhaps by chance, wireless started to work again on the 2.6.31-19 kernel, after I once booted into the Mac OS, and then back into Karmic. 

Could somebody be kind enough to suggest how I might go about diagnosing, obviously in hindsight, what happened? I suppose I should look in the log files, but I have no idea where exactly, and what to look for.

I'd like to overcome this issue a little less randomly and not by fluke, if it were to rear its ugly little head again.

---

### Post by JonPi on 2010-03-16
I have had the same problem, except that it is not random.  I installed 9.10 beta in September and updated it numerous times.  About three times since, I have had to reinstall to get a connection.  The latest was yesterday. It refused to connect after the first update.  I also installed Kubuntu, and it refused to connect before the update.  It will not connect with wired or wireless.

At this point, there is no connection and no terminal to diagnose the problem.  I have rebooted the cable modem, router, and computer.  Normally, this laptop connects to any network, which I need to do because I am a consultant; I cannot take my desktop with me.  We have five machines, all running various 64 bit versions of Ubuntu/Kubuntu (8.04 & 9.10), SUSE, & Debian - all connect.  This machine has had almost every version since 6.10 except 8.10 & 9.04 and I have never had this sort of a problem until -- 9.10.

How can I get a connection?  I can't install new network software without a terminal and connection. Any suggestions?

Jon

---

### Post by faust99 on 2010-03-16
Have you tried getting to a terminal through recovery mode? 

On my machine at least, Karmic has been dismal. I've now got a live DVD (through Remastersys [http://http://www.dedoimedo.com/computers/remastersys.html]("http://http://www.dedoimedo.com/computers/remastersys.html")) and snapshot of a clean, working system, to which I can go back if anything drastic happens again. It might be a bit late for that, but something to keep in mind for future. Remastersys is good because you get a live disk of your own system.

---

### Post by JonPi on 2010-03-16
faust99,

Good suggestions.  I never think of the terminal in recovery mode. I'll have to try that and Remastersys.  Remastersys sounds like it would good to have in my basket.  No good for backup of user files - I have over 800,000 files at my last backup Thursday.  As flakey as 9.10 (Karmic) has been, anyone could really find it useful.  I have done three installs since Thursday and that gets boring, time consuming plus aggrivating.  Can't wait for 10.04 -- maybe it will be more reliable.  I've been using linux since 1997 and unix since 1979 and this has been the worst edition.
 
Thanks for your help.

Jon

---

