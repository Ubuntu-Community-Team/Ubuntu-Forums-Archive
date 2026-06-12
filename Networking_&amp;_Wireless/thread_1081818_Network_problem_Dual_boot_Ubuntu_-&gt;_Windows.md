---
title: "Network problem *Dual boot Ubuntu -&gt; Windows*"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by d.2 on 2009-02-26
hi. Sorry if this thread is already on this forum, but i've searched and didn't find anything ( maybe i did it wrong )

I have a weird problem: If i boot in Ubuntu 8.10 and then i want to boot into Windows, the network card ( WIN ) tells me that " no cable is connected " even if i didn't removed it. If i try to Disable > Enable the network ,or if i insert the cable again .. same problem.

The weird thing is, if i restart Win and enter into Ubuntu.. the network hasn't got any problems. The only " answer " for this is a bit strange.. i must turn OFF the PC, take out the net / AC ( i think ) cable .. and then reinsert them, and turn it on.. if i do this, windows hasn't got any network problem...

I hope you did understand what i was trying to tell you.. Sorry if i have misstyped something.

Thanks for your help,i am waiting for your reply ](*,)

PS : I have Windows XP SP2, Ubuntu 8.10, a PPPOE Connection.. and my motherboard is an ASUS P5LD2-X 1333.

---

### Post by Iowan on 2009-02-27
I've read of the problem going the other way around - Windows drivers don't release control of interface, and won't work when Ubuntu is booted... unless machine is fully powered down first.

---

### Post by johnd126 on 2009-03-11
> **d.2 said:**
> hi. Sorry if this thread is already on this forum, but i've searched and didn't find anything ( maybe i did it wrong )

I have a weird problem: If i boot in Ubuntu 8.10 and then i want to boot into Windows, the network card ( WIN ) tells me that " no cable is connected " even if i didn't removed it. If i try to Disable > Enable the network ,or if i insert the cable again .. same problem.

The weird thing is, if i restart Win and enter into Ubuntu.. the network hasn't got any problems. The only " answer " for this is a bit strange.. i must turn OFF the PC, take out the net / AC ( i think ) cable .. and then reinsert them, and turn it on.. if i do this, windows hasn't got any network problem...

I hope you did understand what i was trying to tell you.. Sorry if i have misstyped something.

Thanks for your help,i am waiting for your reply ](*,)

PS : I have Windows XP SP2, Ubuntu 8.10, a PPPOE Connection.. and my motherboard is an ASUS P5LD2-X 1333.

I have this same problem.  Have you found a fix for it?

---

### Post by d.2 on 2009-03-11
nope,not a thing.. i still do the same on/off thing.:popcorn:

---

### Post by 47_MasoN_47 on 2009-03-11
Does your motherboard support wake on lan?  Maybe turning that off would help.  I currently dual boot Ubuntu 8.10 x64 and Windows XP 32 but I've never had any troubles with that.

---

### Post by gogic on 2009-03-12
I have same problem but internet is ok in windows and not in ubuntu. Same thing with ac cable.

And as Iowan said

> I've read of the problem going the other way around - Windows drivers don't release control of interface, and won't work when Ubuntu is booted... unless machine is fully powered down first.

Any help ?

---

### Post by johnd126 on 2009-03-12
> **47_MasoN_47 said:**
> Does your motherboard support wake on lan?  Maybe turning that off would help.  I currently dual boot Ubuntu 8.10 x64 and Windows XP 32 but I've never had any troubles with that.

No wake on LAN settings in the BIOS but there is one with the XP driver which I have disabled.

What I see is when Ubuntu shuts down the light for this PC on my router turns off.  When I boot into Windows it does not go back on.  If I shut down the computer and unplug the power cord for a bit and plug it back in the light on the router comes back on.  Then I can boot into Windows and it will work.  When I shut down windows the light on the router does NOT go out so it seems that Ubuntu is shutting things down too far.

---

### Post by johnd126 on 2009-03-12
> **d.2 said:**
> nope,not a thing.. i still do the same on/off thing.:popcorn:

That sucks.

I wish there were more settings to configure the network card in Ubuntu.

---

### Post by gogic on 2009-03-12
> **johnd126 said:**
> 
What I see is when Ubuntu shuts down the light for this PC on my router turns off.  When I boot into Windows it does not go back on.  If I shut down the computer and unplug the power cord for a bit and plug it back in the light on the router comes back on.  Then I can boot into Windows and it will work.  When I shut down windows the light on the router does NOT go out so it seems that Ubuntu is shutting things down too far.

There is a trick for u so u dont need to unplug power cord. While in Ubuntu use restart button to restart ur pc and not with software restart and light on router wont turn of :)

This isn't solution but helped me if i need to switch fast.

There are few topic simular on forum but there is no solution, btw which network card do u have ? Realtek  integrated  ?

---

### Post by johnd126 on 2009-03-12
> **gogic said:**
> There is a trick for u so u dont need to unplug power cord. While in Ubuntu use restart button to restart ur pc and not with software restart and light on router wont turn of :)

This isn't solution but helped me if i need to switch fast.

There are few topic simular on forum but there is no solution, btw which network card do u have ? Realtek  integrated  ?

I'v heard it's kind of dangerous to just reboot a Linux system .. the filesystem can get corrupted.  I'd hate to take that chance.

My NIC is an integrated Broadcom 440x built into a Asus Pundit.  Perhaps they're based on the same chipset...

---

### Post by gogic on 2009-03-12
Hell yes !! I fixed my problem and it was with network card 

solution: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

### Post by johnd126 on 2009-03-13
> **gogic said:**
> Hell yes !! I fixed my problem and it was with network card 

solution: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

I can't change mine: it's integrated and it's a Pundit with little expansion.  Plus, this SHOULD work.  It works with Ubuntu, it works with Windows, it's just the dualboot part that fails.  

How can I keep Ubuntu from shutting down the NIC when it leaves??

---

### Post by Bjalf on 2009-10-30
> **johnd126 said:**
> How can I keep Ubuntu from shutting down the NIC when it leaves??

I really, really want to know this, too.

I just clean installed 9.10 alternate, just the command line interface, because I want to install a non-bloated Xubuntu.

When I reboot to XP, the network cable is "unplugged". I didn't have this problem with my previous install, 8.04 Xubuntu, a regular (bloated) install.

Now, when I shut down or reboot, "Deconfiguring network interfaces" flashes past on the screen. How can I stop that from happening? Where is the script that shuts off the NIC? If I reboot into Ubuntu, the network works perfectly, but I have to pull the power **and** disconnect the battery every time I go from Ubuntu to Windows.

I have tried messing around with wake-on-lan settings in XP and BIOS, to no avail.

Aopen 1557 laptop, Broadcom 440x, 9.10 cli only, XP SP3.

---

### Post by Bjalf on 2009-10-31
> **Bjalf said:**
> Where is the script that shuts off the NIC?

Here it is: */etc/init.d/networking*

```
    log_action_begin_msg "Deconfiguring network interfaces"
    if [ "$VERBOSE" != no ]; then
        if ifdown -a --exclude=lo; then
        log_action_end_msg $?
        else
        log_action_end_msg $?
        fi
    else
        if ifdown -a --exclude=lo >/dev/null 2>/dev/null; then
        log_action_end_msg $?
        else
        log_action_end_msg $?
        fi
    fi
```So, how do I exclude both *lo* and *eth0*? My shell programming is a bit rusty.

Edit:
Found this: [http://www.debian-administration.org/articles/122](http://www.debian-administration.org/articles/122) (scroll halfway down)

I'm going to try replacing **--exclude=lo** with **--exclude=lo --exclude=eth0** in both lines.

Later.

---

### Post by Bjalf on 2009-10-31
> **Bjalf said:**
> Here it is: */etc/init.d/networking*

```
    log_action_begin_msg "Deconfiguring network interfaces"
    if [ "$VERBOSE" != no ]; then
        if ifdown -a --exclude=lo; then
        log_action_end_msg $?
        else
        log_action_end_msg $?
        fi
    else
        if ifdown -a --exclude=lo >/dev/null 2>/dev/null; then
        log_action_end_msg $?
        else
        log_action_end_msg $?
        fi
    fi
```

**Yes!**

I am awesome!    :cool:

Booted Ubuntu, replaced both ```
--exclude=lo
``` with ```
--exclude=lo --exclude=eth0
``` in */etc/init.d/networking*, rebooted back to Windows XP, and the network worked perfectly!

Now please excuse me, I have to strut around and brag about my mad skillz for a bit.

:biggrin:

---

### Post by stinger30au on 2009-10-31
> **Bjalf said:**
> **Yes!**

I am awesome!    :cool:

Booted Ubuntu, replaced both ```
--exclude=lo
``` with ```
--exclude=lo --exclude=eth0
``` in */etc/init.d/networking*, rebooted back to Windows XP, and the network worked perfectly!

Now please excuse me, I have to strut around and brag about my mad skillz for a bit.

:biggrin:

excellent

well done

---

### Post by stevevp on 2010-01-01
Hi, I've got exactly the same problem. Have just installed Ubuntu 8.10 in Windows XP sp2 (couldn't get 9.10 to install so will update when I've got 8.10 working). The install went ok apart from the sound not working. Internet browsing seemed faster than under windows. On booting back to Windows I found I had the cable unplugged error and no internet connectivity. The power off reboot detailed above seems to do the trick but the more graceful edit to the network config file doesn't. I'm a complete newbie in all this so could some kind soul please confirm that I have understood the file edit which should now read precisely as follows:
>     log_action_begin_msg "Deconfiguring network interfaces"
    if [ "$VERBOSE" != no ]; then
        if ifdown -a --exclude=lo --exclude=eth0; then
        log_action_end_msg $?
        else
        log_action_end_msg $?
        fi
    else
        if ifdown -a --exclude=lo --exclude=eth0 >/dev/null 2>/dev/null; then
        log_action_end_msg $?
        else
        log_action_end_msg $?
        fi
        net_flag_down
    fi
    ;;Many thanks.

---

