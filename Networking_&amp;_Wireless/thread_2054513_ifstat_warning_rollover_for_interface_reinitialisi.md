---
title: "ifstat warning rollover for interface reinitialising"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by GNU-Cody on 2012-09-07
Hello all, I'm not sure if this is a serious problem or not but, surprisingly, I could find no mention of it on the Ubuntu forums, so I am posting one.(<-- If I missed the post about this issue in my searches please let me know!) The specific message I am receiving is...

[FONT=Courier New]ifstat: warning: rollover of interface bond0 reinitialising[/FONT]

I would like to know... 
  **#1** - Exactly what is causing the error?
  **#2** - Is this a symptom of a potentially serious problem?
  **#3** - What can I do, if anything, to correct it?

**My findings on other sites:**
[SourceArchive.com's ifstat data.c page]("http://ifstat.sourcearchive.com/documentation/1.1-8/data_8c-source.html") seems to show that the message is only generated when the [FONT=Courier New]ifstat_quiet[/FONT] variable isn't initialized properly. I saw no obvious reason that the variable wouldn't be initialized on every run but the programmers coded a test checking for it with a warning message  so they must have their reasons for doing so. I guess this could mean that there is a bug in [FONT=Courier New]ifstat[/FONT]? ...but I'm not *code-worthy* enough to say for sure. 



*Now for some explanations...*

**The command I am entering that generates the message is:**
[FONT=Courier New]ifstat -a -S -i bond0[/FONT]

**My project:**
I am testing channel bonding 4 NICs on Ubuntu 12.04 Server i386. Primarily, I am determining how much of a throughput increase I can achieve on my local network infrastructure. (Further details about my setup are below.) Everything has gone very smoothly during testing. The NICs bonded without issue and throughput immediately increased from &#8776;11.4MB per sec to &#8776;28MB per sec. This is the only warning message I have received. The commands I am using to test the throughput are...
_*On the server with the channel bonded NICs:*_
  First I setup three netcat listeners with...
[FONT=Courier New]    nc -l 2221 > /dev/null &
    nc -l 2222 > /dev/null &
    nc -l 2223 > /dev/null &[/FONT]
  Then I run ifstat to watch the KBs per sec like so...
[FONT=Courier New]    ifstat -a -S -i bond0[/FONT] 

_*On each of 3 transmitting workstations:*_
  I simply transmit dummy data to one of the 3 listening ports on the server...
[FONT=Courier New]    yes "TestData" | nc 192.168.0.10 *[portNum]* [/FONT]

**System specs:**
*(Don't laugh! ...Okay, go ahead and chuckle if you wish, just remember this is a testing rig so it's made up of old but fully functional equipment. *:smile:* )*
Intel P4 2GHz
768MB RAM
4 10/100 NICs (channel bonded [FONT=Courier New]balance-rr[/FONT])
IDE HDD
Ubuntu 12.04 Server i386 (fully installed w/latest updates)

Thanks in advance for your efforts in solving this! :KS

---

