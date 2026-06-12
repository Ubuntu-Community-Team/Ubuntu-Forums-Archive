---
title: "Novat-T 500 and LNA activation"
date: 2013-03-10
forum: Mythbuntu
---

### Post by drifting on 2013-03-10
Hi Chaps

Not quite sure what has been going on of late, might have been an update somewhere down the line, or the local seagulls have been dancing on my aerial again? But I am suffering from digital breakup, and pauses, as if the signal was dropping (Myth shows strength at around 60%)

Anyhoo, noticed that the /etc/modprobe.d/options  which had the following in :- options dvb_usb_dib0700 force_lna_activation=1


Had been renamed to bak, with no other file to replace it? Did read that later versions of Ubuntu used
 options.conf, so promptly created the file. Do difference?

Then read about another option usbcore.autosuspend=-1 as I have had the issue where one of the Nova's tuners would suddenly stop working, the only option would be a cold reboot.  I followed the instructions to add this to the kernel boot.

Same result. 

Anyone any ideas? or is it time I just threw this out and went for something a bit newer (Suggestions on card very welcome)
Ubuntu 12.04 LTS With Mythbuntu .26

Regards Paul

---

### Post by AlecJ on 2013-03-10
I think the signal has been breaking up over the last few days in Kent generaly, I get Freesat from Astra for Mythtv but also freeview on a bedroom tv, both have been playing about?
BBC news just freezes for a few seconds every so often.
So I think it them not us.
The fact Mythtv shows 60% would suggest your card is ok.
 Mythtv only shows 75% from a 90cm dish it was lower on the 45cm dish.
Freeview, I can see the Bluebell Hill mast from my house, about 5 miles as the crow flies, but the TV only shows 65%?

I still have a Nova T, good card, removed it as I went to satellite for the better picture quality.

---

### Post by PhilWig on 2013-03-10
I've found the T500 to be very stable and it would be a pity to give up on it too soon.

I use LNA but not the autosuspend in /etc/modprobe.d/options.conf (but I found it worked with both 9.04 and 12.04 in /etc/modprobe.d/options anyway).  The reference to the .conf version is way down the text in:

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#Forcing_the_activation_of_LNAs_.28Low_Noise_Amplifier.29](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#Forcing_the_activation_of_LNAs_.28Low_Noise_Amplifier.29)

Two issues I've noted:

a) the gain, even with the LNA turned on is low compared with the DVB-T TV.  Around Christmas I had the sort of breakup you mention and after lots of trial and error finally put it down to a faulty downlead - possibly water in it.

b) If you change configuration such as turning LNA on or even switching from VGA to HDMI output or vice-versa it is necessary to cold boot for it to work.  ie close down, power off at wall, press power button to discharge PSU,  wait 20 secs, power on at wall and boot up.  This forces a microcode reload.

Hope you fix it.
Phil

---

### Post by drifting on 2013-03-11
Hi Guys

Thanks for the information. Was not aware of any problems in Kent, probably down to to the triple dip recessions and snow! AlecJ, like you I also have two DVB-S2 cards, and they are connected straight to an tiny sky dish, do not have the least problem with the Sat channels. All my issues relate to the Nova-T 500.

PhilWig, thanks for the information on the options.conf, did not seem to make the slightest bit of difference to my signal strength, hence like you I followed the info on Linuxtv. 

Down lead, would not have thought so, was only fitted in October, tend to think that the likely suspect is the gulls, the buggers treat the aerial as a landing pad. See if I can get someone round to check the strength. But the freeview TV's around the house seem fine.

Regards Paul

---

