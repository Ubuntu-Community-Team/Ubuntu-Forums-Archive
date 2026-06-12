---
title: "Wireless Card not found - module not installed?"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by greymoose58 on 2006-06-09
I originally posted this in the Dapper forum but it closed down before I got any feedback. Sorry about the double post.

My daughter has a Linksys WMP54G wireless card installed in her machine. It was chosen partly because there are so many entries related to installing it in these forums.

We've succesfully installed the driver and ndiswrapper but when we run ndiswrapper -l it says the driver is present but nothing about the hardware. I know the card is there.

After hours of fruitless research I am forced to conlude that I can't figure it out. 
The next day.....

Ok. I've worked out that I probably don't have the correct modules loaded. We did a clean install and I assumed that they would load as we went. I've reached the end of my technical knowledge now. How do I find and install the correct module for wireless adapters?

Cheers.

---

### Post by Patsoe on 2006-06-10
I don't know much about this card... but I'll try to help :)
Can you perhaps associate the driver with the right device by using the -d option of ndiswrapper? You can type "ndiswrapper" without options to get a usage description.

---

### Post by greymoose58 on 2006-06-11
[QUOTE=Patsoe]Can you perhaps associate the driver with the right device by using the -d option of ndiswrapper? You can type "ndiswrapper" without options to get a usage description.[/QUOTE]

When I used -d I got a list of options that mean very little to me. :confused:  I vaguely understand what they mean but have no idea how to apply them. The same thing happens when I enter ndiswrapper without options although I understand a bit more.

Would it be possible to explain your suggestion step by step?

Cheers.

---

### Post by Patsoe on 2006-06-11
To start with, I should say I'm not sure this will work, but here goes...

Type "lspci" in a terminal, and look up the entry that shows your wifi card. The address at the start of the line is important. Now, type "lspci -n", which will give you the same address list but now with some strings behind them in the format XXXX:XXXX. Get the string that is listed with your card's address.

No you're going to tell ndiswrapper to use the driver you installed with the device you just looked up. The command is "ndiswrapper -d XXXX:XXXX drivername" where you have to replace XXXX:XXXX by the value you obtained above (duh), and drivername should be replaced by the name that you see when you ask "ndiswrapper -l".

Hope it works! I'm off to bed, see ya.

edit: well, almost off to bed :)
I just wanted to add you can use the PCI-ID (the XXXX:XXXX thing) to look up some tips here: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) - just search the page for the PCI-ID.

---

### Post by greymoose58 on 2006-06-14
[QUOTE=Patsoe]Type "lspci" in a terminal, and look up the entry that shows your wifi card. [/QUOTE]

Thanks for the suggestion Patsoe but I didn't get past the first step. There is no entry for a wifi card. I suspect I have done something wrong with the installation process.

---

### Post by noname101 on 2006-06-14
Try to modprobe ndiswrapper.
```
sudo modprobe ndiswrapper
```
Also post the output of lspci and lsmod.

---

### Post by greymoose58 on 2006-06-15
I'll be glad to post those outputs but the situation has changed a bit so I thought it would be worthwhile checking if you still need the same information.

The machine will now only boot up as far as configuring network devices where it hangs. This only seems to happen if the network cable is not plugged in. It is dual booting at the moment so I booted into windows where I was informed that new hardware (the wifi card) had been found. I'm guessing that the machine has finally decided to recognise the card and Ubuntu is having problems figuring it out. When I boot into rescue mode and do ndiswrapper -l it still shows the driver but no hardware. 

Does this change things much or do you still need the sme information?

Thanks for your help.

---

### Post by noname101 on 2006-06-15
When booting click ctrl c to stop it from trying to configure the ethernet. Its basically trying to get an ip address from ethernet but doesn't work because its not connected. Do you know what version of your linksys WMP54G card it is? Also if you could post the output of lspci and lsmod, it might help.

---

