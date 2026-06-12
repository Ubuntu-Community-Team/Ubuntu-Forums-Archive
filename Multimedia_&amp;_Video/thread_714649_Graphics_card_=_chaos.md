---
title: "Graphics card = chaos"
date: 2008-03-04
forum: Multimedia &amp; Video
---

### Post by comingbackdown on 2008-03-04
My friend just brought me an Nvidia Geforce 4 MX 4000.
I played hell installing it on Windows XP, but it works.

Ubuntu, however...
It recognized it, pulled up the restricted drivers window. It installed the drivers, and told me to reboot. Okay, so I rebooted. My sister's boyfriend had already told me to expect being dumped to the command line and having to do some reconfiguring. He was right. It booted, and dumped me directly to the terminal. That wouldn't be a problem, if it hadn't frozen. I had no choice but to hold down the power button and reboot. I go back to boot up Ubuntu, and get a screen where it's starting things up.


It gets to something about executing boot scripts, and just sits there. You can type things, but it's not really a command line/shell.

Also, I used to have problems with even the simplest 2D Ubuntu games freezing. I suspected the graphics card. Now I have the newer card, so I think it'll be alright if I can get it working. I do have one other issue though. When the games would freeze, I'd go to the virtual console with the intent of killing the rogue process. The problem: The virtual console was in a really small (like 640x480) resolution, and I couldn't see all of the text. I'd use the shortcut to get back to desktop (which I've since forgotten), the console would scramble... Explanation: The text would start to disappear, but it'd freeze up with a few nonsense characters on the screen. I could go to any of the virtual consoles, but not desktop, and they were all too low res for me to see enough to use them.

Help me please. I'm getting to the point where I can to basic stuff with no problem (I installed at least ten games all through the terminal, no problem.) but this one threw me. Bigtime.

Note: The Nvidia card is set as default in the bios. My preferred resolution is 1024 x 768, which is what I'm trying to obtain. I also have my onboard graphics card, and I'd like to set it up to use both cards for a dual-monitor setup if possible. Until I get this sorted out, I'm stuck on Winblows... Oy... :( 
"Windows: Good for gaming, bad for peace of mind."

---

### Post by sanddgroper on 2008-03-04
Hi comingbackdown
Dont think you can run an onboard card and a nvidia card together.
Thats a pretty old card which means it may struggle  with ubuntu.
Try disabling the onboard graphics then try getting the nvidia card
to work.

Cheers
Sandy

---

### Post by Yellow Pasque on 2008-03-04
First off, disable your onboard video in BIOS. NOw boot. When you get stuck at that "boot scripts" screen, press Ctrl+Alt+F1 to get to the terminal.

Run these commands:
```
sudo update-pciids
lspci | grep VGA
```

Note the PCI ID of the Nvidia card.

Now edit your /etc/X11/xorg.conf file with vim (sudo apt-get install vim ,if needed)
```
sudo vim /etc/X11/xorg.conf
```
Now press 'i' to put vim in text editing mode. Go to your Device section and make sure there is a Busid and "nvidia" drive line. For example
```
Section "Device"
        Identifier      "Generic Video Card"
        Busid           "PCI:x:y:z"
        Driver          "nvidia"
EndSection
```
For the Busid line, enter the 3 numbers you got from the lspci command. So if the lspci said:
> 01:05.0 VGA compatible controller...
you would enter it as
> Busid    "PCI:1:5:0"
When you're done editing, press 'Esc' to return vim to command mode. Now enter :x (colon, x, Enter) to exit vim and save your changes. Now reboot and pray.

---

### Post by comingbackdown on 2008-03-04
I printed those instructions, and I'm about to go try them.

Note: The BIOS doesn't offer "Enabled/Disabled", it offers "Enabled/Auto". So, if the onboard won't die, I guess I'll have to figure out an alternate way to use it with Win.

Just so I've got this straight...

It doesn't have that line in the config file, so since it's listed as my primary card in my bios, it's trying to use it, doesn't have that line, so the window manager fails and dumps me to command line (or in the case of after I rebooted, doesn't start, so I have to access the command line) ?

I do need to set my virtual terminal to a higher resolution... It's impossible to read it all, as some of it is off screen.

---

### Post by comingbackdown on 2008-03-04
I had it working. I edited just like you said, and it worked. I was fiddling with some of the graphics options, got a reboot prompt. Okay... I had a feeling that was not good. I log back in, and... Well...
My desktop background wasn't there. I tried to pull up terminal and go see if anything in xorg.conf had changed. Well, I couldn't since the terminal wasn't visible. Nothing was. Anything graphical other than the main menus wouldn't work.

So, I rebooted, went into recovery mode...

I checked all of the display settings in xorg.conf

Here's what I found. Somehow, both graphics cards got listed with the pci bus id of the Nvidia,
PCI:1:5:0
and, the Intel is listed as "Default Screen", but with the monitor "Gateway EV700" that's connected to the Nvidia.

What did I screw up, and what did I do? It worked fine until I messed with something, but I don't know what I did or how to fix it. Heeeeelp!

I had it working, and I know I can get it working again with a little help.

---

### Post by sanddgroper on 2008-03-04
Hi
Do you have a manual for the computer does it say how to
install the addon graphics.
I would think untill you know that the onboard card is disabled
then all bets are off.
If you know the make and model of your motherboard you could
look on the web for a manual for it to see how to install an addon
graphics card

Cheers
Sandy

---

### Post by comingbackdown on 2008-03-04
Onboard is disabled, kinda. It's not set as default.

I did have it working, 100%, but I messed up something when I was adjusting the graphics settings.

I can type out and post a text copy of the xorg.conf if necessary.

---

### Post by erginemr on 2008-03-05
> I can type out and post a text copy of the xorg.conf if necessary.

And please tell us how you have installed the NVIDIA card's driver? Using the driver "nvidia-glx" from Synaptic (not "nvidia-glx-new") just works.

I've been using GeForce 4 MX as well, but am away from my home computer now...

---

### Post by comingbackdown on 2008-03-05
I installed the first driver it popped up in the restricted drivers manager.

Here's my xorg.conf, and all the copies of it...

I put it in a .tar via Windows 7zip.

It took me a while to get them.

---

### Post by sanddgroper on 2008-03-05
Hi comingbackdown

In those xorg.conf files all I see is the intel board I dont see any nvidia board.
but I do see the intel board trying to use nvidia drivers.
What happens if you try to run the intel board with the intel i810 driver.
Like I said until you can disable the onboard graphics I dont think you will get the
nvidia card to work

Cheers
Sandy

---

### Post by comingbackdown on 2008-03-05
I've gotta be able to use both cards in Windoze though... Maybe if it's BIOS related, I can just switch it and reboot when I need them both in Windoze. I'll do some research. Maybe I could try removing the Nvidia, rebooting, getting Ubuntu stable again, and taking another whack at it.

AFAIK, the onboard can't be disabled. The BIOS options are either Onboard, or Auto. My friend has some Dell knowledge, and he pretty much told me "You get 'Onboard', 'Auto' looks for a PCI card."

---

### Post by sanddgroper on 2008-03-06
Ok best of luck with it.
How widows handles two different types of graphic cards at once I dont
know.

Cheers
Sandy

---

