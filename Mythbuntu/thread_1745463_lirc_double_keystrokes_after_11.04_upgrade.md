---
title: "lirc double keystrokes after 11.04 upgrade"
date: 2011-05-01
forum: Mythbuntu
---

### Post by ederopaa on 2011-05-01
I am experiencing double keystrokes with my remote after 11.04 upgrade. It kind of makes using MythTV with a remote hard. Everything worked fine before the upgrade in 10.10. I've already tried changing delay and repeat variables in my mythtv lirc file without results. Maybe I've tried the the wrong variables. 

I've also tried this:

```

  begin
    prog   = mythtv
    button = Up
    config = echo '' > /dev/null
    config = Up
    repeat = 3
  end

``` 

This kind of works but still tends to skip two menu objects.

Any ideas or similar problems?

---

### Post by YfoMp5QBh2 on 2011-05-01
Just updated to 11.04 from 10.10. Having exactly the same problem too after the update but I am using XBMC instead.

Can anybody help please?

---

### Post by YfoMp5QBh2 on 2011-05-01
Ok forget it. I found a fix in the forums. Read this threat and it will fix the problem.

[http://ubuntuforums.org/showthread.php?p=10709651#post10709651](http://ubuntuforums.org/showthread.php?p=10709651#post10709651)

---

### Post by ian dobson on 2011-05-01
Hi,

I also had double keypresses from my remote. I just edited the remote configuration file /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge and deleted all but one of the remotes. That solved it for me.

Regards
Ian Dobson

---

### Post by Nausser on 2011-08-08
> **ian dobson said:**
> Hi,

I also had double keypresses from my remote. I just edited the remote configuration file /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge and deleted all but one of the remotes. That solved it for me.

Regards
Ian Dobson
> Ok forget it. I found a fix in the forums. Read this threat and it will fix the problem.

[http://ubuntuforums.org/showthread.p...1#post10709651](http://ubuntuforums.org/showthread.p...1#post10709651)
I've tried the previous fix of adding the line to "/etc/rc.local" which did fix it unless I restarted lirc after the system was running. Also, I couldn't seem to add any irexec or irxevent files to the config without breaking the control for Mythbuntu.
So I tried the first quote of removing all but one remote from the lircd.conf.mceusb file. The was about a hauppauge remote I presume. This fix actually didn't work for me at all.
I tried to remove lirc altogether and configure it myself, manually (that's what I had to do to get the ir blasting for my cable box working correctly). 
I just wanted to put the word out that a better and more perminant solution must be available. I will keep working on my end to try to sort things out. If anyone stumbles on this and has an idea, please let me know.

---

### Post by rileyp on 2011-08-09
> **Nausser said:**
>  Also, I couldn't seem to add any irexec or irxevent files to the config without breaking the control for Mythbuntu..
The button names you use must be in the "list" to get the list stop lirc  and type ```
irrecord -l
```If you use std naming method for the buttons you wish to add it will not break! I found this out about a week ago....  Strange but true... 
 > **Nausser said:**
> I tried to remove lirc altogether and configure it myself, manually (that's what I had to do to get the ir blasting for my cable box working correctly). .
Me too and I found out the only way a button will be recognized in irw is to use std naming convention...Did you get irsend to work ? Are you using a mceusb?
What really irritates me though is that in the mythbuntu install it uses the no std naming convention and it works... We add a button and sorry no go...
Perhaps there must be a file somewhere that is resolving the std key/button naming convention back to the actual mce button names eg key_one back to 1 If thats correct?? 
  > **Nausser said:**
> I just wanted to put the word out that a better and more perminant solution must be available. I will keep working on my end to try to sort things out. If anyone stumbles on this and has an idea, please let me know. I just want to know what the heck is going on as I had lirc all under control and now my shoes have been stolen...

---

### Post by mathog on 2011-08-09
> **rileyp said:**
> 
   I just want to know what the heck is going on as I had lirc all under control and now my shoes have been stolen...

I vaguely recall reading somewhere that the double keystrokes issue was due to a module being installed in the newer kernel and then it being loaded again by the lirc start up script.  Or maybe it was a user land version being loaded.  In any case, that problem was the result of essentially running the same code twice.  When you are seeing double keystrokes use lsmod and ps -ef  and see if there are two receivers running.

---

### Post by PatrickD-52761 on 2011-09-04
> **mathog said:**
> I vaguely recall reading somewhere that the double keystrokes issue was due to a module being installed in the newer kernel and then it being loaded again by the lirc start up script.  Or maybe it was a user land version being loaded.  In any case, that problem was the result of essentially running the same code twice.  When you are seeing double keystrokes use lsmod and ps -ef  and see if there are two receivers running.

I would try the wiki page for MythTV that's referenced in the other thread. It talks about the repeating keystrokes (which I had also), and it discusses issues with IR Blasting.  Here's a [link]("http://www.mythtv.org/wiki/MCE_Remote#Arrow_Buttons_Repeat") to the page itself. That should take you right to the arrow repeating issue, and the IR Blasting issues are below that.

Have a great weekend everyone, and hope this helps:)
Patrick.

---

### Post by rileyp on 2011-09-05
My ir remote reciever/transmitter works fine now. It turned out the transmitter part of my device was faulty. Only took me 2 weeks to work this out.... :(
cheers rileyp

---

### Post by DylanW75 on 2011-09-14
I've also been having this same problem, though with a fresh install of Mythbuntu 11.04 and a Dvico Fusion MCE USB remote. One other difference I have is that I do not have a /sys/class/rc directory and using lsmod does not turn up and ir related modules.

To troubleshoot I've had irw running while using the remote in MythTV and although irw reports only single presses MythTV reacts as if each button was pressed twice. Also running **netstat -A unix** turns up only two connections to the lirc socket, one of which would be irw as it disappears once irw is terminated.

So I'm at a loss as to what is going on, I'm hoping that someone can shed some light on this problem or suggest some further troubleshooting steps for me to try.

Thanks in advance!

---

### Post by DylanW75 on 2011-09-15
Righto, I've located the cause of my double-press problem. The auto-generated file ~.lirc/mythtv (which is linked to ~.mythtv/lircrc) had duplicate entries for each of the remote's buttons, deleting the duplicates has solved the issue.

---

### Post by sqeelurgle on 2011-09-30
Brilliant, sorted.  I had the double entries in .lirc/mythtv as well

Thanks

---

