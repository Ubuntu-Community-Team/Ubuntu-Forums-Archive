---
title: "HD 5450 video card installation help"
date: 2011-09-18
forum: Multimedia Software
---

### Post by hollywoodpete on 2011-09-18
Fairly new to Ubuntu. I just installed a new Gigabyte HD 5450 ATI video card and it doesn't seem to be recognize at all. Any help would be great. I have searched, googled and reboot at least 100 times over the last 2 days.

---

### Post by coffeecat on 2011-09-18
Hi. First thing to say is that the HD5450 GPU should work out of the box in Ubuntu 11.04, and give you compiz and Unity with the default open source driver. I have a HD5450 in the machine I'm posting from now.

So - which version of Ubuntu are you running? What exactly do you mean by it not being recognised? Can you see it in the BIOS? Were you able to run Ubuntu before you installed the Gigabyte, and if so what was the video chipset you were using then?

---

### Post by hollywoodpete on 2011-09-18
> **coffeecat said:**
> Hi. First thing to say is that the HD5450 GPU should work out of the box in Ubuntu 11.04, and give you compiz and Unity with the default open source driver. I have a HD5450 in the machine I'm posting from now.

So - which version of Ubuntu are you running? What exactly do you mean by it not being recognised? Can you see it in the BIOS? Were you able to run Ubuntu before you installed the Gigabyte, and if so what was the video chipset you were using then?

Thanks for your interest in my problem. I am using 11.04. It does not show up in the Bios boot sequence. I have been able to run Ubuntu both before and after installing the card but only from the onboard video.

---

### Post by hollywoodpete on 2011-09-18
There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.

I also get this message

---

### Post by coffeecat on 2011-09-18
OK. I'm logging off in a moment - it's very late here. I'll post what I can and pick this thread up in the morning.

If the card doesn't show up in the BIOS then this does sound like a BIOS issue. Some things to check. Fit the card and move your VGA/DVI cable to the Gigabyte card. Sorry to state the obvious, but I've forgotten to do this and wondered why things were not working! :)

Next - start the machine and enter the BIOS. If you don't get any signal at all at this stage with the video cable plugged into the PCIe card, then either the card is faulty or the PCIe slot is faulty. Make sure the card is seated in properly.

If you can get into the BIOS, make sure the onboard video is disabled. Many/most BIOSs do this automatically when you plug a PCIe card in, but in some you need to change some BIOS settings yourself. I can't be more specific - BIOSs vary.

If you do succeed in getting the BIOS to recognise this card, I think you'll find it to be very satisfactory. It gives you all the desktop effects you need with the default open source driver. Speaking of which, if and when you do get to the Ubuntu desktop, the Additional Drivers utility will soon pester you to install the proprietary driver. If everything is working OK and you don't game, then don't bother.

Lastly - if the onboard video is nvidia and you have installed the proprietary nvidia driver, this needs to be uninstalled before you boot up with an ATI card, otherwise the GUI may fail to load.

---

### Post by hollywoodpete on 2011-09-18
I removed the card and re installed it. I went to the synaptic package manager and searched NVIDIA and removed everything there.

The motherboard is Biostar 945CG-V4 Bios is AMI

No luck so far

---

### Post by coffeecat on 2011-09-19
I didn't notice your post #4 when I posted last night - perhaps we posted simultaneously - otherwise I wouldn't have concentrated on the BIOS. Mention of the catalyst control centre suggests you tried to install the proprietary driver for ATI cards. I suggest you purge the system of all proprietary drivers and associated packages so that it uses the default open source video drivers. As I mentioned before, this works well with that card.

Have a look here:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Try the full "Problem: Need to fully remove -fglrx and reinstall -ati from scratch" option. Post back if you need help with that. It might need one more step, but try that and let us know how you get on.

---

### Post by hollywoodpete on 2011-09-19
I tried the full purge as described. No luck. If it helps any I noticed the fan is not running on the card

---

### Post by coffeecat on 2011-09-19
I won't be able to help you with the fan because my card is a passively cooled fanless one. 

But I'm having trouble following exactly what you are doing. I'm assuming you've now got the card recognised in the BIOS and that your monitor is connected to the 5450 PCIe card and not to the onboard video. Am I correct so far? If you then try to boot up, how far do you get? What do you see? Do you get anything? Do you see the grub menu? Does the GUI fail and dump you to a text console? Do you get an error message?

---

### Post by hollywoodpete on 2011-09-19
> **coffeecat said:**
> I won't be able to help you with the fan because my card is a passively cooled fanless one. 

But I'm having trouble following exactly what you are doing. I'm assuming you've now got the card recognised in the BIOS and that your monitor is connected to the 5450 PCIe card and not to the onboard video. Am I correct so far? If you then try to boot up, how far do you get? What do you see? Do you get anything? Do you see the grub menu? Does the GUI fail and dump you to a text console? Do you get an error message?

The card is still not recognized by BIOS. The only way I get a video feed is through the onboard video.

---

### Post by coffeecat on 2011-09-19
> **hollywoodpete said:**
> The card is still not recognized by BIOS. The only way I get a video feed is through the onboard video.

I wasn't sure. Reconfiguring drivers isn't going to help. See what I posted earlier. If it's not being seen in the BIOS, then it's most likely a faulty card or faulty PCIe slot.

Is it brand-new? Can you try it in another machine?

---

### Post by .... on 2011-09-19
> **coffeecat said:**
> If it's not being seen in the BIOS, then it's most likely a faulty card or faulty PCIe slot. Can you try it in another machine?
Seconded. The other suggestion I have is updating to the latest BIOS and reloading the default settings. Make sure the BIOS is not set to initialize/use the onboard video first. Most BIOS's have a GPU preference setting, but usually the default setting prefers discrete GPU.

Oh, and I guess when you boot with onboard video, you can check lspci or lshw to see if the card is being seen, but onboard used instead.

---

### Post by .... on 2011-09-19
> **hollywoodpete said:**
> I tried the full purge as described. No luck. If it helps any I noticed the fan is not running on the card
Sorry, I just read that. It definitely sounds dead. I recommend returning it and getting a fanless 6450 or Nvidia GT430/520 (unless you're okay with fan noise). Are you planning to do any gaming in Ubuntu or are you using Windows for gaming?

---

### Post by coffeecat on 2011-09-19
> **.... said:**
> Sorry, I just read that. It definitely sounds dead. I recommend returning it and getting a fanless 6450 or Nvidia GT430/520 (unless you're okay with fan noise). Are you planning to do any gaming in Ubuntu or are you using Windows for gaming?

I concur that a replacement is probably needed. However, if the OP wishes to stay with a HD5450 there is at least one fanless version on the market. @hollywoodpete, I have the Asus EAH5450 Silent with 512MB of DDR2. Works for me! :) But I'm not a gamer.

---

### Post by hollywoodpete on 2011-09-19
Thanks for your help. The card is being RMA ed to newegg.

---

