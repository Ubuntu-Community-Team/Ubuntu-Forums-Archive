---
title: "Grub2 is not automatically booting default OS"
date: 2010-09-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Brian Vaughan on 2010-09-07
Since I upgraded from 10.04.1 to 10.10 beta, Grub2 is no longer automatically booting the default OS. There's no indication of the expected ten second countdown -- Grub2 just sits there until an option is chosen.

I kept the version of /etc/default/grub that I'd used before the upgrade. Before the upgrade, I'd made some minor changes to enable displaying the Plymouth splash at full resolution. Here's what I'm using:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Brian 2010 May 16
GRUB_GFXMODE=1024x768-32
GRUB_GFXPAYLOAD_LINUX=1024x768-32

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by zika on 2010-09-07
> **Brian Vaughan said:**
> Since I upgraded from 10.04.1 to 10.10 beta, Grub2 is no longer automatically booting the default OS. There's no indication of the expected ten second countdown -- Grub2 just sits there until an option is chosen.

I kept the version of /etc/default/grub that I'd used before the upgrade. Before the upgrade, I'd made some minor changes to enable displaying the Plymouth splash at full resolution. Here's what I'm using:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Brian 2010 May 16
GRUB_GFXMODE=1024x768-32
GRUB_GFXPAYLOAD_LINUX=1024x768-32

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
Either move to another place */boot/grub/gribenv* or ```

sudo grub-editenv /boot/grub/grubenv create
```

---

### Post by Brian Vaughan on 2010-09-07
That didn't seem to make a difference.

That is, I executed the command, then rebooted; I removed /boot/grub/grubenv, executed the command, then rebooted.

---

### Post by ranch hand on 2010-09-07
I would save any customised files to a safe place and do a total removal of grub (if you have a reliable connection).

I would;
```

sudo apt-get purge grub-pc grub-common

```
Then I would delete the /etc/boot/grub file

Then;
```

apt-get install grub-pc grub-common

```
DO NOT attempt to reboot before completing that last step or you will have no way to boot at all.

Do not do any messing with the resolution just set up your time out as you want it.  You might want to remove "splash" in your /etc/default/grub file just to make sure that graphics can be less of a problem.  Set your default for sure.

If you have MS on board I would save the menu entry for it from your /boot/grub/grub.cfg file before doing anything so that if there is a problem you have that.

This is a better version of grub and I suspect that the upgrade got some corruption in there somewhere.  A clean install of grub should go very smoothly and give you a better grub.

---

### Post by Brian Vaughan on 2010-09-07
The re-installation of grub went smoothly -- and I'm glad to see the diagnostic messages while booting again -- but I'm still not getting the timeout.

Another problem I've been having, which I've assumed is unrelated, is that when I select my name from a list via gdm, the first time after booting, the screen flashes, and I get the same gdm menu a second time. I've guessed that somehow the graphic display on tty7 has an error, and is restarted on tty8. I mention it here just on the off chance it is related somehow -- otherwise, I'll start a separate thread.

---

### Post by ranch hand on 2010-09-08
That is strange.

Do you still have splash enabled?

What video card or controller do you use?

What driver do you use?

---

### Post by cariboo on 2010-09-08
I noticed one of my systems was sitting at the grub menu and it didn't autostart either, I didn't pay to much attention, as I busy doing something else. 

I'll see what it does when I start it up in the morning.

---

### Post by VinDSL on 2010-09-08
> **Brian Vaughan said:**
> Since I upgraded from 10.04.1 to 10.10 beta, Grub2 is no longer[...]I'm dual-booting 10.04.1 and 10.10...

It's been my experience that 10.10 doesn't like the 10.04.1 grub, and vice-versa.  That is, I can build grub with 10.04.1 and 10.10 doesn't like it.  Or, I can build grub with 10.10 and 10.04.1 doesn't like it.  So, you have to choose one and live with the other.

The only success I've had is totally wiping grub, and starting from scratch.  I do this after every kernel update.

Here are the commands that I use (in run order):

```
$ sudo mv /boot/grub /boot/grub_backup

$ sudo apt-get purge grub grub-pc grub-common

$ sudo mkdir /boot/grub

$ sudo apt-get install grub-pc grub-common

$ sudo apt-get clean

$ sudo grub-install -v

$ sudo update-grub

$ sudo grub-install --recheck /dev/sda
```

I'm too tired to give a line-by-line tutorial.  If you don't know what these commands do, you shouldn't be using them.  ;)

Once I'm confident that the old grub has been wiped, and the new grub is installed, I do a system restart, and life is beautiful.

This works with 10.04.1 and 10.10

Have fun!

---

### Post by ranch hand on 2010-09-08
I would like to know if there is any change in the behavior after the upgrades to libplymouth2 and plymouth this morning.

---

### Post by cariboo on 2010-09-08
I checked the system that seemed to hang yesterday, it started up as normal this morning, it may be due to the fact that I upgraded 129 packages yesterday.

---

### Post by Brian Vaughan on 2010-09-08
I tried VinDSL's instructions -- as far as I can see, just a variation of ranch hand's. It didn't make any change, either. This was after this morning's batch of system updates.

I've tried this with and without my resolution settings, with and without the splash screen. No differences.

I'm using the current proprietary Nvidia driver. I'm not seeing any display glitches or other weird behavior -- it's simply that Grub isn't automatically booting the default operating system. If I select it, everything proceeds as normal.

The gdm issue is separate. Apparently, it has to do with an Apache2 module emitting an "stty reset" command. Obviously, that's well after Grub has done its job. A fix is in the works:
[https://bugs.launchpad.net/bugs/626723](https://bugs.launchpad.net/bugs/626723)

---

### Post by ronparent on 2010-09-08
What is your 'GRUB_TIMEOUT=' in /etc/default/grub?

---

### Post by Brian Vaughan on 2010-09-08
> **ronparent said:**
> What is your 'GRUB_TIMEOUT=' in /etc/default/grub?

GRUB_TIMEOUT=10

(Which is the default.)

---

### Post by drs305 on 2010-09-08
Brian,

Looks like it's time to run the boot info script!

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")


Added:

If you want to see if bypassing GRUB_TIMEOUT and recordfail check produces a boot after 5 seconds, you can temporarily change this section of /etc/grub.d/00_header:

> 
#[COLOR="DarkRed"]cat << EOF[/COLOR]
#[COLOR="DarkRed"]if [ \${recordfail} = 1 ]; then[/COLOR]
#[COLOR="DarkRed"]  set timeout=-1[/COLOR]
#[COLOR="DarkRed"]else[/COLOR]
#[COLOR="DarkRed"]  set timeout=${GRUB_TIMEOUT}[/COLOR]
#[COLOR="DarkRed"]fi[/COLOR]
#[COLOR="DarkRed"]EOF[/COLOR]
cat << EOF
if [ \${recordfail} = 1 ]; then
  set timeout=5
else
  set timeout=5
fi
EOF

Save and run update-grub.

This bypasses both settings, so it may not be something you would want to keep permanently, but it should provide an uninterrupted boot after 5 seconds of whatever your default OS is. Of course, you can change the value to any positive countdown value you desire.

---

### Post by Brian Vaughan on 2010-09-09
I've attached the RESULTS.txt file that bootinfoscript produced, which I ran before making the changes to 00_header that drs305 suggested.

After editing 00_header as suggested, running update-grub, and rebooting, I still didn't get a timer or any automatic booting. If I read it right, it's forcing the timer.

One peculiarity: before editing, 00_header had
```
set timeout=${2}
```
instead of
```
set timeout=${GRUB_TIMEOUT}
```



So at this point, I'm wondering if it's some sort error that's sending a keypress, like a hardware error with my keyboard or somesuch. I don't see anyone jumping in to say that they're having the same problem.

---

### Post by VMC on 2010-09-09
I noticed your RESULTS.txt file show sdb having grub2  install, and on partition #3, but that partition no longer exists.

Also, is your BIOS set to boot sda and **not** sdb? If you have a record fail there will be no timeout.

---

### Post by drs305 on 2010-09-09
> **Brian Vaughan said:**
> I've attached the RESULTS.txt file that bootinfoscript produced, which I ran before making the changes to 00_header that drs305 suggested.

One peculiarity: before editing, 00_header had
```
set timeout=${2}
```
instead of
```
set timeout=${GRUB_TIMEOUT}
```

So at this point, I'm wondering if it's some sort error that's sending a keypress, like a hardware error with my keyboard or somesuch. I don't see anyone jumping in to say that they're having the same problem.

The difference you noted is just a change in Grub 1.98. 

Your actual files appear to be in good shape. Here is what I would recommend: purge all of Grub and then install it again. It is a very simple process and the only caveat is that you have a steady Internet connection and good power supply, as you will momentarily lose your bootloader.

Can you currently get to a normal Ubuntu operating system? If not, do you have a LiveCD?

---

### Post by Brian Vaughan on 2010-09-09
I believe I found the problem.

While tweaking the settings under 9.10 or 10.04, I had edited /etc/grub.d/00_header, and following my usual practice, I had first copied the file to /etc/grub.d/00_header.dist. I think that 00_header.dist was pre-empting or overriding the settings in 00_header.

When I removed 00_header.dist, the problem cleared up, and I got the timeout counter, etc., as expected.

I'm guessing the change I'd made to 00_header had been irrelevant, and the two files were otherwise similar enough before this upgrade that there hadn't been a problem.

I'm not sure how to account for grub being installed to a non-existent partition. I had chosen to install grub to both hard drives, following the play-it-safe suggestion in the dialogues. I gather grub doesn't necessarily designate drives the same way Linux proper does. Anyway, it doesn't seem to be causing any trouble.

Thanks for the help, everyone.

---

### Post by drs305 on 2010-09-09
Multiple files can cause problems but it's rare enough that it seldom comes up. An example of this is making copies of custom files or backing up the scripts in /etc/grub.d. If they are still executable they will be run - and whichever is run last may overrule earlier scripts.

Glad you solved it. It would be helpful if you marked the thread SOLVED via the Thread Tools link at the top right of the first post.

---

