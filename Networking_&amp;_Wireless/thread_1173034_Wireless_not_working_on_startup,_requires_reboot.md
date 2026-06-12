---
title: "Wireless not working on startup, requires reboot"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by KingNeil on 2009-05-29
Whenever I start up my Dell XPS M1530 on Ubuntu 9.04, the wireless network does not work. It does not show my network. The only way I can get it to work is by restarting the computer.

Clearly, I do not want to have to restart the computer every time I start it up.

How do I fix this?

---

### Post by KingNeil on 2009-05-29
By the way, I've discovered that this is to do with power.

If I shut down the computer with the power supply plugged in, but then start it up WITHOUT the power plugged in, it doesn't work and requires a restart. Otherwise, it works fine.

So basically, the computer needs to be started up in the same state as it is shut down, which clearly is a problem.

---

### Post by KingNeil on 2009-05-30
Does no one have a solution for this?

---

### Post by Chris_no on 2009-05-30
I would take a look at the services running.

You can try disabling the powernowd if you have it enabled.

It manages powerusage to cpu and stuff to save power when powercable are out
it can make things go slow sometimes.

I turned it off on my netbook because it made my apps slow when the battery
was low.

Turn it on again if it doesn't help.

---

### Post by KingNeil on 2009-06-01
I don't have powernowd enabled in services. 

For some reason, whenever I turn on the laptop when it's unplugged, the Wifi does not work. There's clearly some kind of power setting, but I don't know what it is.

---

### Post by KingNeil on 2009-06-01
In the Ubuntu Help And Support section, it says this:

5.2.1.&#8195;Check that the device is on

   1. Many wireless network devices can be turned on or off. Check to see if there is a hardware switch, some devices can be switched off from Windows and may need to be turned back on from Windows.

---------------

Only problem is: I don't have Windows on here at all. Ubuntu is my only OS. There is no dual partition.

Somehow, my power settings are turning the Wifi off in the event that it's been inactive for a certain amount of time. Problem is: I cannot see any setting to alter this. I've looked in my BIOS, I've looked in Ubuntu's Network Manager. Nowhere can I see any setting for this.

Again, let me reiterate. My Wifi works fine. It just doesn't work if it's been inactive for a while. Then I have to restart the computer and it works fine. This is very annoying.

By the way, it is an Intel PRO/Wireless 3945ABG

---

### Post by KingNeil on 2009-06-02
Wow... still no one has a solution. I've provided a lot of info.

---

### Post by NilsE on 2009-06-02
Boot up in BIOS and see if there is a power saver setting to disable the wireless when on battery or for that matter anytime.

---

### Post by KingNeil on 2009-06-05
> **NilsE said:**
> Boot up in BIOS and see if there is a power saver setting to disable the wireless when on battery or for that matter anytime.

Nope, the only power setting in my BIOS is is something called "USB wake support", which lets USB devices wake up the system from sleep.

By the way, to reiterate: there is a switch on the side of my laptop that turns the Wifi on and off, but it only works if the Wifi is switched on at startup. The switch always is able to toggle the Bluetooth on/off, but not the Wifi. For some reason, the Wifi just doesn't start up sometimes, so I require a reboot of the machine. Anyone got another solution?

---

### Post by Gausian on 2009-06-05
try this...

```
sudo modprobe -r iwl3945
```

then

```
sudo modprobe iwl3945
```

see if that brings it to life.

---

### Post by KingNeil on 2009-06-05
> **Gausian said:**
> try this...

```
sudo modprobe -r iwl3945
```

then

```
sudo modprobe iwl3945
```

see if that brings it to life.

What do those commands actually do? I don't like running commands without knowing the effects.

---

### Post by Gausian on 2009-06-05
first command turns off the driver (if on at all)

iwl3945 is the default driver for your card
-r = remove

second command will call it back up. reset and refreshed.

---

### Post by KingNeil on 2009-06-05
> **Gausian said:**
> first command turns off the driver (if on at all)

iwl3945 is the default driver for your card
-r = remove

second command will call it back up. reset and refreshed.

OK, and is there any way to call this command on startup, since this is the problem. Also, it prompts for my password, so I don't know how I could get that to run at startup without asking for a password.

By the way, the first command disconnected the Wifi as expected -- but then froze my computer, after which the caps lock and some other symbol with a downward arrow continually flashed on my keyboard. I had to turn off the computer with the power button and start up again

---

### Post by Gausian on 2009-06-05
ok, something other than the driver is the problem.  reloading the wifi driver doesnt make computers crash unless something else wrong.

---

### Post by Gausian on 2009-06-05
Do you use a bluetooth mouse by chance?  I remember reading somewhere that this can cause flashing caps and scroll buttons in some cases.

Might be worth a try, to disconnect it if you are using one.

---

### Post by KingNeil on 2009-06-05
> **Gausian said:**
> Do you use a bluetooth mouse by chance?  I remember reading somewhere that this can cause flashing caps and scroll buttons in some cases.

Might be worth a try, to disconnect it if you are using one.

I do in fact use a wireless mouse, so I guess that's bluetooth. I'll give it a try.

By the way, I shouldn't even need to use the disconnect command you gave, only the reconnect one.

What I really want to know is how I could have this run on startup.

---

### Post by Gausian on 2009-06-05
you can run sudo commands/scripts at startup with no need for password by adding them to your /etc/rc.local file...

```
gksudo gedit /etc/rc.local
```

the reason i had you run modprobe -r first was to unload the driver in case it loaded with faults.  then start it up fresh with just the modprobe command.

---

### Post by KingNeil on 2009-06-05
> **Gausian said:**
> you can run sudo commands/scripts at startup with no need for password by adding them to your /etc/rc.local file...

```
gksudo gedit /etc/rc.local
```

the reason i had you run modprobe -r first was to unload the driver in case it loaded with faults.  then start it up fresh with just the modprobe command.

OK, thanks for that tip.

By the way, I unplugged the mouse and ran the remove command, but it still froze the computer.

Aaaanyway, I'm going to try adding the second command to my startup and I'll let you know if I have any problems.

---

### Post by KingNeil on 2009-06-05
Btw do I add my command BEFORE or AFTER "exit 0"?

---

### Post by KingNeil on 2009-06-05
I want to add that the command does not work, period. Another solution is needed.

As you said, "something other than the driver is the problem. reloading the wifi driver doesnt make computers crash unless something else wrong."

Does anyone have any other ideas?

---

### Post by KingNeil on 2009-06-06
Anyone? Maybe a reinstall of the BIOS?

---

### Post by ixpl on 2009-06-06
I had this this issue also and found that it was network manager. It only happened with my Toshiba Satellite M45. I noticed it was whenever i changed locations. I think it saves someting in the RAM because i would have to power down remove the battery and hold power button for 30 seconds or so to clear the RAM. I fixed it with  sudo apt-get install wicd in 8.10 i had to add the wicd repos. it works great keeping my laptop from connecting to any unsecured network like network manager war notorious for. only problem with it was connecting to a hidden was difficult even with the ssid put in the settings, and i am sure there's a fix for that somewhere.

---

### Post by KingNeil on 2009-06-08
I've been using a temporary solution, whereby I put my computer into "Suspend" mode instead of shutting it down. That seems to work well, but still, I'd like to know what the problem is.

---

