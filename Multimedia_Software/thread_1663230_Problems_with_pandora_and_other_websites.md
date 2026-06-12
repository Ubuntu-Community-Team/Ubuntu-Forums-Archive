---
title: "Problems with pandora and other websites"
date: 2011-01-09
forum: Multimedia Software
---

### Post by yogi1983 on 2011-01-09
hello folks,
I'm about to pull my hair out. I installed a new hard drive last week and loaded lucid 2.6.32-27 on to it. Everything has worked fine until yesterday, I can't get Pandora to load all the way. So off to the Google gods and the forums. 

Every one said to uninstall the flash plug in's and reinstall. went through the software center and installed the restricted extras. Restarted Firefox. Still nothing. 
Someone suggested that i try a link that went to adobe that would check if i had the correct flash player and if it was working. Adobe said it was. So i installed adblock plus. Nothing.

Also installed Chrome to see if it was something in Firefox. I just don't know. i can throw dvd's in, they play. 

The only thing I'm not sure about is if it has something to do with the 64-bit install and the plug-in's for it.
i have checked 100 times it SHOULD not have any thing to my system. All my hardware is 64-bit compatable. 

Any help would be great

Intel core2 6400@ 2.13GHz
Intel DQ965gf mother board
4gb ram
ATI FireGl v5600 work station card

---

### Post by lovinglinux on 2011-01-09
I don't have access to Pandora, but I would try the 64bit square preview plugin.

You can easily install it using my [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") extension, which removes any conflicting plugin, install the 64bit from Adobe by default and apply some tweaks.

---

### Post by pme 72 on 2011-01-09
I just checked that site and it loaded without issue on Lucid 32 bit.

---

### Post by yogi1983 on 2011-01-09
hello
so i tried the flash-aid. no go. but now every time i open Pandora it opens an empty page as well.

I have 32-bit Ubuntu on several other computers and have never ran in to this.
thanks
yogi

---

### Post by lovinglinux on 2011-01-09
> **yogi1983 said:**
> hello
so i tried the flash-aid. no go. but now every time i open Pandora it opens an empty page as well.

I have 32-bit Ubuntu on several other computers and have never ran in to this.
thanks
yogi

It seems you haven't executed Flash-Aid after installation. You need to click the "Execute" button to run the installation/removal script. Also make sure "Gnash", "SWFdec" and "Adobe from repositories" are selected in the "Removal Options" tab, because you have these 3 different plugins installed. Firefox is detecting Gnash as primary, which is causing the issues. It needs to be removed, along with the other 2 plugins, in order to be replaced with the 64bit square preview from Adobe.

Please let me know if you get any errors in the terminal output, when running Flash-Aid script.

---

### Post by yogi1983 on 2011-01-09
thank you kind sir you are the man!  with the test option there i figured if the test didnt seem to work why would the ad on. 
Nice and simple fix  
thanks 
yogi:popcorn:

---

### Post by lovinglinux on 2011-01-10
> **yogi1983 said:**
> thank you kind sir you are the man!  with the test option there i figured if the test didnt seem to work why would the ad on. 
Nice and simple fix  
thanks 
yogi:popcorn:

Nice to read that. Although you have fixed your problem, I would like to know which problems did you get in the "Test" mode?

---

### Post by yogi1983 on 2011-01-10
hello,
when i hit test the terminal opened, asked for password, and then ran. at the end it asked me to close the browser. and when i opened it back up the browser still would not any steaming media to come through. 

should i have kept the browser open?

thanks,
yogi

---

### Post by lovinglinux on 2011-01-11
> **yogi1983 said:**
> hello,
when i hit test the terminal opened, asked for password, and then ran. at the end it asked me to close the browser. and when i opened it back up the browser still would not any steaming media to come through. 

should i have kept the browser open?

thanks,
yogi

No, you did it right. Please generate a new report.

Does it works on other web sites?

---

