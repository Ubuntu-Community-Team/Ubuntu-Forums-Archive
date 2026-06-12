---
title: "VST in 64-bit?!?"
date: 2008-03-21
forum: Multimedia Production
---

### Post by JR_Moneybags on 2008-03-21
Simple question - Can you run VST plug ins on a 64-bit installation of Feisty? If yes, PLEASE tell me how.

I have tried to install DSSI-VST with no success.

I'm surprised that this one is proving so hard to find the answers for - what with all the different 64-bit studio distros getting around now. Surely I'm not alone trying to get the VST's to run?


Cheers
JR_Moneybags

---

### Post by cmay on 2008-03-26
hi 
if you can read the online linuxmagazine there was an article on 64studio and how the vst plugins could be used.
however i think that vst is for windows and ladspa plugins are for linux. you can write plugins for audacity yourselve and the nyquist prompt can also be used. 
when i recorded under windows i used vst plugins alot but i nerver tried on linux.

i am not a linuxaudio expert yet.
hope this helps

---

### Post by Stochastic on 2008-03-27
From what I remember, in order to get vst running on a 64-bit install you'll need to use 32-bit libraries in your compiling process - if that even works.  But why bother with such a strange combination of software???  upgrade to 32-bit or use LADSPA (and why feisty?).

Here's an old howto I wrote on getting fst to work in ubieStudio feisty32: [http://ubuntuforums.org/showthread.php?t=557466](http://ubuntuforums.org/showthread.php?t=557466)
don't know if that helps at all?

Edit: furthermore why aren't you using UbuntuStudio if you have audio needs?  I'd first upgrade to UbieStudio gutsy (or hardy comes out in a month) before worrying about configuring vst plugins.

---

### Post by JR_Moneybags on 2008-03-29
Thanks for the help. I have the gutsy 32 bit disk here but I am hanging out for the Hardy release and possibly Hardy Studio if I can get it.

At the risk of starting a rant over the state of broadband access in rural Australia - I rely on getting my distros from magazines. I can't download them for myself here on a 28.8k connection. As yet I haven't seen a UbieStudio disk . I did pick up the 64studio disk a few months back but decided against it.

Okay. I think for now I will try LADSPA and look at moving over to 32-bit UbieStudio when the new one comes out.

** PS - If there's anyone in Australia that has a copy of UbieStudio that they'd like to post to me, I'd be very appreciative.

---

### Post by Stochastic on 2008-03-29
You'd be more likely to find someone willing to post you a copy if you go asking around the Ubuntu Australia LoCo Team website: [http://ubuntu.org.au/](http://ubuntu.org.au/)

---

