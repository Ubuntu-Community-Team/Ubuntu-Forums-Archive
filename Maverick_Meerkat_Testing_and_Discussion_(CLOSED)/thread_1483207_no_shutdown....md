---
title: "no shutdown..."
date: 2010-05-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zika on 2010-05-14
Am I the only one that, still, has the problem with shutdown...? It started during Lucid testing and it has not been solved, yet, at least not for me... Any ideas, news...?

---

### Post by plun on 2010-05-14
Strange error :confused:

Can you see any error with a terminal shutdown ?

```
sudo shutdown now
```


--

---

### Post by dino99 on 2010-05-14
this is the same here:
- stop work
- reboot: close the session but no post, so need a cold boot
- start: generally the first 2 failed and the 3d is ok

all that mess start at karmic a2 with grub2, udev vs hal, ext4

i've seen on launchpad that an old bug about python ( pointers not deallocated) and still not fixed, could be the reason or one of.

---

### Post by taavikko on 2010-05-14
In what way does this manifest?
After hitting "shutdown" it throws you back to gdm?

I had that issue in LL, but as being an blunt instrument I went ahead and cleared my ~/.* which cured it. ((had other issues as well))

---

### Post by dino99 on 2010-05-14
***  cleared my ~/.*  *****

i'm afraid to do that, so much reconfs then :(

---

### Post by Ctulhu on 2010-05-14
I had the same problem on at the end three different computers (cf. related post here). I could shutdown properly again once I disabled the OpenOffice systray starter.

---

### Post by zika on 2010-05-14
When I choose Shutdown or issue shutdown now -P all file-systems are un-mounted, everything is in freeze and Plymouth rotates lights. I have to do HW off...

---

### Post by zika on 2010-05-14
> **Ctulhu said:**
> I had the same problem on at the end three different computers (cf. related post here). I could shutdown properly again once I disabled the OpenOffice systray starter.I think I do not have OO sys-tray starter, at least not that I know of...

---

### Post by ranch hand on 2010-05-14
With this new kernel things are working better for me on boot up but shutdown still takes a long time.

The problem you are having sounds very like the one I had (probably have) that makes me to scared to put "splash" back in my menu entry.

Try;
```

echo "Adding Lounge on sda7" >&2 
cat << EOF
menuentry "Lounge on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet
        initrd /initrd.img
}
EOF

```
edited for you box for the partition (and tittle if you want) in your custom file and see if it works.

The real problem, I think, is libplymouth2 because it just takes for ever to shut ever little thing down.  Without the splash on boot, you do not have one on shut down and while is still takes for ever at least it doesn't freeze.

Or you could just edit the menu for a single boot to not have "splash" using "e".

I would try it and see.

I have 2 entries for this OS and am going to use the one with splash in it next time I reboot.  If it screws with me I will file a new bug on libplymouth2 with this new kernel.

It seems to work a lot better on my clean installs of 10.04 either as 10.04 or upgraded to 10.10.  At least it works with the splash without freezing.  It is faster with no splash there too.

---

### Post by zika on 2010-05-14
If, only, problem would be so simple...
Of course, I've tried all that, as You could, probably, remember, while we were in Lucid testing...
No errors are shown, only ordinary stuff, weak f-systems unmounted and so on... and then, nothing, for minutes... OK, I never was patient enough to go over two or three monutes, but no disk activity, tty switching works, no possibility of logging, Alt-SysRq-b works and so on...

---

### Post by ranch hand on 2010-05-14
Yup, I mainly put all that on for folks who may have missed it.

I am actually impressed with the improvements in performance of Plymouth et al.  I still think the easiest way to fix the bugger is drop it as soon as possible for just about anything else.

Xsplash and whatever libs it needs would be fine.

Just to rub salt in your wounds, here on the Stoned Lizard (10.10 upgrade) the new kernel dropped my boot speed a good 25%.  From around a minute to 44.74 seconds.

I even reinstalled ureadahead and it actually helps instead of adding a consistent 15 seconds to my boot.  Now it seems to be good for knocking off about 8 to 10 seconds.

---

### Post by plun on 2010-05-16
> **zika said:**
> If, only, problem would be so simple...
Of course, I've tried all that, as You could, probably, remember, while we were in Lucid testing...
No errors are shown, only ordinary stuff, weak f-systems unmounted and so on... and then, nothing, for minutes... OK, I never was patient enough to go over two or three monutes, but no disk activity, tty switching works, no possibility of logging, Alt-SysRq-b works and so on...

Have you tried different shutdowns ?

From man shutdown


>        -r     Requests that the system be rebooted after it has  been  brought
              down.

       -h     Requests  that  the system be either halted or powered off after
              it has been brought down, with the choice as to which left up to
              the system.

       -H     Requests  that  the  system  be halted after it has been brought
              down.

       -P     Requests that the system  be  powered  off  after  it  has  been
              brought down.


---

### Post by zika on 2010-05-16
> **plun said:**
> Have you tried different shutdowns?I've tried -P, -h since that is the only thing I want. The rest are not... At least, from the explanation given from them...

---

### Post by Docaltmed on 2010-05-18
No shutdown for me, either. I get to the splash screen, the dots light up one by one until we get to the next-to-last red dot...and there we sit. No further action.

Tried "sudo shutdown -P now", got the exact same response. I haven't seen any error messages.

This is a pretty stupid and annoying error. I've tried all of the recommended workarounds, e.g.modifying GRUB with splash, quiet splash, nosplash, splashupyournose...and yes, I recompiled after each change. No improvement.

I'm quite willing to entertain any additional suggestions.

---

### Post by frenchy82 on 2010-05-18
Hi,

You can find two suggestions there
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/576204]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/576204")

Maybe it could help

---

### Post by zika on 2010-05-18
Tried them all... In Lucid... (testing phase)...

---

### Post by philinux on 2010-05-18
Are there no clues at all in the log files?

---

### Post by ranch hand on 2010-05-18
As I understand it libplymouth2 is responsible for the things like getting the system log written.

If this is true it would explain why my most recent one is from the 11th.

---

### Post by zika on 2010-05-18
> **philinux said:**
> Are there no clues at all in the log files?Nope. I'll try to locate any once I get some spare {morning,afternoon}. I've noticed that last message before shutdown-freeze iz about un-mounting weak file systems. If I press Ctrl-Alt-Del, it awakens and next message is about unattended upgrade... then some other and it goes into reboot... It stalls somewhere between these two...

---

### Post by ranch hand on 2010-05-18
Ah, that is the problem.  The weak file systems are too strong.

Unattended upgrades, the concept itself gets on my thungas.  But it would make testing a lot more interesting.  I wonder it you can set it just to accept all "partial upgrades".  That would even be a better idea.

---

### Post by Milos_SD on 2010-05-19
I can't shutdown or restart my PC from gnome (Indicator Applet Session) only if it was turned on more then couple of hours. There is only one thing I can do then: restart X with ctrl+alt+backspace -> shutdown/restart from GDM. My friend have that problem on his laptop too.

P.S. I don't have the problem like zika, here nothing happends when I click on restart/shutdown, I can continue working on it.

---

### Post by crjackson on 2010-05-19
I only have a shutdown/logoff/restart problem when OOo QuickStarter is enabled and showing in the notification area.  The instant I close that, the problems are gone for me.

---

### Post by zika on 2010-05-20
> **crjackson said:**
> I only have a shutdown/logoff/restart problem when OOo QuickStarter is enabled and showing in the notification area.  The instant I close that, the problems are gone for me.No OOo here...

---

### Post by cariboo on 2010-05-20
I've had a problem for the last couple of days, where choosing shutdown from the menu causes the system to reboot. I haven't had time to troubleshoot the problem yet.

---

### Post by mick222 on 2010-05-20
Had the same problem from beta lucid thought it might be hardware related or to do with grub2 . I have to switch my computer of at the mains to get it to shutdown .Same thing happens with other distros and suse so not sure what to do next. Tried all the suggestions on launchpad and here but no luck startup also takes an age. I messed around with xorg edgers for a while could that have messed up my system ? I even went as far as reseting the BIOS to see if that would help.

---

### Post by ranch hand on 2010-05-20
Is suse using plymouth now.  Been a while since I last tried it.

I would bet this is all a libplymouth2 problem and if suse is using plymouth I think that would pretty much prove that.

I have not tried the newest Mandriva but I have 2009-1 on here and it does not use plymouth and there is no problem there.

---

### Post by zika on 2010-09-03
Just to refresh this "standing problem"...
First, yes, it still **_*doesn't work*_**...
Accidentally I found a patch for this:
In Terminal: **sudo shutdown now**
After I get CLI garbadge from DMSG (GUI shut down, no sight of Plymouth, even though it works properly otherwise, this is only if I issue shutdown from Terminal) press **Ctrl-Shift-Alt** and voilà machine shuts down...
No "regular" way works.
Funny enough, on a laptop, where shutdown works properly, this "method" does not work, it gets me into restart... :)

---

### Post by cariboo on 2010-09-03
It may be a problem with your hardware, as I have 4 different computers running maverick, and three of them shut down but have text instead of plymouth, all three use nvidia cards. The fourth one shuts down with out a plymouth error, it runs an Intel 945 graphics adapter.

---

### Post by zika on 2010-09-03
I do not think that there is HW problem, other LiveCD's work properly...
It is not a big deal, it just lasts too long... (started with Lucid, I think in testing....) :)
BTW, I'm not the only one with that problem, I think there are several threads about that (not here)...

---

### Post by zika on 2010-09-25
Recent upgrade broke that trick that I was using to shut-down "properly"... ;(
I presume it was plymouth that did that...

Update: Oh boy, it is better that I thought. Yes, upgrade broke the trick, but, now, shutdown works properly. Great. Thanks!!!

---

### Post by tjeremiah on 2010-09-26
I dont know what caused it but I think the problem started two days ago. I can no longer shutdown without holding down the power button. Also, shutting down fromt the terminal doesnt work.

---

### Post by cariboo on 2010-09-26
Do you can any output in the terminal when you try:

```
sudo halt -h now
```

Other than the system is shutting down?

---

### Post by tjeremiah on 2010-09-27
I updated last night, dont know what solved it, but its no longer an issue. I can shutdown and restart without issue.

---

### Post by cariboo on 2010-09-27
Glad to see the problem solved itself.

---

### Post by zika on 2010-09-27
I knew it. It lasted just a couple of days. Back to shutdown on a switch... :(

---

### Post by 23dornot23d on 2010-09-29
Interesting - I only usually shutdown from the shutdown icon on the menu bar .....

But I tried a 

**shutdown now**

It gave me the blue screen asking me to resume etc .....

Almost felt like its possibly not unmounting the USB drives ........ 

( as this is the only other instance that I can recall - other than a network problem .... that has ever managed to hang my system )



I say this about unmounting - because I have them right next to me and can hear them and see the lights flashing ..... 
[COLOR=Red]**( but the resume - menu came up so quick .... it had no chance to have done anything else ..... )**[/COLOR]
is there a way of debugging this .... using trace .... or something similar .... how often do people shutdown from the command line ?

______________________________________________

Not sure if this helps anyone ..... but thought I would try it out ..... to see if I had the same or similar problem ..... 

and I do ..... from the above terminal command ...... shutdown now ( but I do not use this - other than to test it !!! )

The only feed back was as I pressed resume after the incident  .... [LINK]("http://img842.imageshack.us/img842/91/dscf4554forweb.jpg")


**@zika** ..... out of interest does 

**reboot**

work ok .......... 
(reason just wondering if the unmounting and mounting of drives works ok in this instance)

---

### Post by zika on 2010-09-30
If I do **sudo shutdown now** in Terminal, I can, after it goes blank or settles, issue Ctr-Alt-Del and get a shutdown (powerdown).
If I do GUI shutdown it just hangs and Ctr-Alt-Del gives me reboot.
**reboot** works OK, I think, both ways (CLI and GUI)...
For several days, several days ago, it worked as it should... For the first time in a long time, from middle of Lucid testing...

---

