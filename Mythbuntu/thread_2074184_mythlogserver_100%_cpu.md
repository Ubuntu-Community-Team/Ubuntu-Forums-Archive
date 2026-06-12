---
title: "mythlogserver 100% cpu"
date: 2012-10-21
forum: Mythbuntu
---

### Post by deadite66 on 2012-10-21
Upgraded to 0.26 yesterday using the mythbuntu ppa.

randomly mythlogserver is hitting 100% cpu, anyone else had this problem?

got a bash script killing it if it goes above 40% but that's not ideal is it.

---

### Post by odror on 2012-10-24
> **deadite66 said:**
> Upgraded to 0.26 yesterday using the mythbuntu ppa.

randomly mythlogserver is hitting 100% cpu, anyone else had this problem?

got a bash script killing it if it goes above 40% but that's not ideal is it.

I have the same issue with 12.10

---

### Post by Hidyman on 2012-11-25
> **deadite66 said:**
> Upgraded to 0.26 yesterday using the mythbuntu ppa.

randomly mythlogserver is hitting 100% cpu, anyone else had this problem?

got a bash script killing it if it goes above 40% but that's not ideal is it.

Would you mind sharing that script as a quickfix?
I'm a newbie and I am also having this problem.
It causes my backend box to get very loud :(.

---

### Post by deadite66 on 2012-11-25
sure, i run this as root every 5 minutes.
if the service is more than 40% it will be killed and email will be sent to my root Maildir, shouldn't be too hard to adjust as needed.

```
#!/bin/bash
mythlogload=`top -b -n1 |grep mythlogserver |head -n1 |awk -F' ' '{ print $9 }'`
#echo $mythlogload

if [ $mythlogload -gt 40 ]; then
	kill `pidof mythlogserver`
	echo "Killed mythlogserver" |mailx -s 'Killed mythlogserver' root@sakura
fi

```

---

### Post by Hidyman on 2012-11-26
I kept getting an error about it expecting an integer, so I modified it.
I hope this works.

```
#!/bin/bash
mythlogload=`top -b -n1 |grep mythlogserver |head -n1 |awk -F' ' '{ print $9 }'`
mythlogload=$( printf "%.0f" $mythlogload)

if [ $mythlogload -gt 80 ]; then
     kill `pidof mythlogserver`
     echo "Killed mythlogserver"
fi
```

---

### Post by Hidyman on 2013-02-11
> **Hidyman said:**
> I kept getting an error about it expecting an integer, so I modified it.
I hope this works.

```
#!/bin/bash
mythlogload=`top -b -n1 |grep mythlogserver |head -n1 |awk -F' ' '{ print $9 }'`
mythlogload=$( printf "%.0f" $mythlogload)

if [ $mythlogload -gt 80 ]; then
     kill `pidof mythlogserver`
     echo "Killed mythlogserver"
fi
```

Somehow I typed 80 instead of 40 should be:

```
#!/bin/bash
mythlogload=`top -b -n1 |grep mythlogserver |head -n1 |awk -F' ' '{ print $9 }'`
mythlogload=$( printf "%.0f" $mythlogload)

if [ $mythlogload -gt 40 ]; then
     kill `pidof mythlogserver`
     echo "Killed mythlogserver"
fi
``` I foud this out because myhtlogserver was hovering at 70 so it never flagged the script to kill it.
Just wanted to update in case someone else is having this problem.

I have experienced a new problem though, once in a while I'll have about 20 mythlogserver instances running, each using %4 or so.
I'm about to research and see if I can remove logging altogether.

---

### Post by luciferin on 2013-02-12
Please keep us posted Hidyman.  I've been trying things like crazy for the last week and can't solve this problem.  It causes serious problems on my (admittedly under-powered system).  Commercial flagging is at <2fps for instance.  

So far I've tried setting --nodblog and setting --loglevel err
These two seem to reduce the frequency of the problem, but it still happens within an hour. Note: I haven't actually timed it, so it could be placebo effect here.

I've also tried switching to the syslog-ng for the logging backend (--syslog local7).  This did not help at all.



*EDIT:
So, I just removed the mythlogserver executable.  So far I haven't noticed any problems (other then the fact that myth is no longer logging anything, but what's the point of logging if it causes my system to cease functioning?).

I'll update if I notice any complications.

---

### Post by deadite66 on 2013-02-17
Shame their doesn't seem to be much interest from the devs to sort this problem.

---

### Post by Hidyman on 2013-03-20
> **luciferin said:**
> Please keep us posted Hidyman.  I've been trying things like crazy for the last week and can't solve this problem.  It causes serious problems on my (admittedly under-powered system).  Commercial flagging is at <2fps for instance.  

So far I've tried setting --nodblog and setting --loglevel err
These two seem to reduce the frequency of the problem, but it still happens within an hour. Note: I haven't actually timed it, so it could be placebo effect here.

I've also tried switching to the syslog-ng for the logging backend (--syslog local7).  This did not help at all.



*EDIT:
So, I just removed the mythlogserver executable.  So far I haven't noticed any problems (other then the fact that myth is no longer logging anything, but what's the point of logging if it causes my system to cease functioning?).

I'll update if I notice any complications.

Thanks for the info.

Instead of deleting the file i used chmod -x to make it unable to execute.

For other people having this problem, it is located in /usr/bin
Go to /usr/bin and sudo chmod -x mythlogserver
I haven't found any problems in doing this yet.
An update could reset the file permissions. I'll keep an eye out for that.

I wish the developers would make this an option that we can control in setup.
I understand the need for logging, but if the logging itself is causing the problem then something is wrong.
If my setup is working as expected, I should be able to turn logging off altogether.

A disclaimer:  I'm a real newbie when it comes to Linux so if I'm doing something dumb, please let me know.

I'll update if anything changes.

---

### Post by tgm4883 on 2013-04-18
> **deadite66 said:**
> Shame their doesn't seem to be much interest from the devs to sort this problem.

Is there a bug report?

---

### Post by deadite66 on 2013-04-18
[http://code.mythtv.org/trac/ticket/11230](http://code.mythtv.org/trac/ticket/11230)

---

### Post by jksj on 2013-04-18
This problem has been discussed extensively on mythtv-users the relevant thread is :-
[http://www.mythtv.org/pipermail/mythtv-users/2013-March/347650.html](http://www.mythtv.org/pipermail/mythtv-users/2013-March/347650.html)
The issue seems to be related to the log failing and restarting due to a file permission problem. Hope the link is of help.

---

### Post by Hidyman on 2013-07-02
It is as I feared.  Updating has changed the permissions back to executable, so if you are using this as a workaround you will need to change the permissions after updating.
I'm removing the file for now.  If anything breaks I'll update.

---

### Post by tgm4883 on 2013-07-02
> **Hidyman said:**
> It is as I feared.  Updating has changed the permissions back to executable, so if you are using this as a workaround you will need to change the permissions after updating.
I'm removing the file for now.  If anything breaks I'll update.

That thread that was posted states that using syslog works, which is what we do.

---

### Post by deadite66 on 2013-09-21
upgraded to myth 0.27 and mythlogserver is gone, presumably disabled with the compile option --disable-mythlogserver.
many thanks mythbuntu packagers.

---

