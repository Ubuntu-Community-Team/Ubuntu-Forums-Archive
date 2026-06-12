---
title: "flash still kills firefox 3.0!!!"
date: 2008-06-25
forum: Multimedia Software
---

### Post by MedellinManDem on 2008-06-25
After going on Myspace and Youtube, Firefox still closes down unexpectedly when I go on flash based sites...

Is there a fix for this or not?

---

### Post by SledgeHammer_999 on 2008-06-25
how did you install flash?

---

### Post by fred_miller on 2008-06-25
I had lots of problems with flash on firefox too, it says that  i need flash to view movies on you tube, but when i click the the install bar on the browser page it says it's already installed.  So i installed seamonkey and the firefox theme for it and other than the silly ship's wheel it's firefox and it works and has all the useful plugins already installed.

---

### Post by MedellinManDem on 2008-06-25
> **SledgeHammer_999 said:**
> how did you install flash?

Everything was installed prior to me using firefox 3 as per the help/to-do guides on this very forum.

Afaik, the flash problem with youtube has never been resolved.

---

### Post by SledgeHammer_999 on 2008-06-25
> **MedellinManDem said:**
> Everything was installed prior to me using firefox 3 as per the help/to-do guides on this very forum.

Afaik, the flash problem with youtube has never been resolved.

Can you be more specific? Can you tell me the exact way you did it? Maybe in the installation process you followed, it resulted in something being borked!

---

### Post by MedellinManDem on 2008-06-25
> **SledgeHammer_999 said:**
> Can you be more specific? Can you tell me the exact way you did it? Maybe in the installation process you followed, it resulted in something being borked!

I don't remember. Can you just tell me the best way to install it and I will purge my current setup.

---

### Post by underground on 2008-06-25
I did the following and the problem dissapeared...goto synaptic,search for libflash and from the results remove anything is installed...hope it will help you..

---

### Post by SledgeHammer_999 on 2008-06-25
Go to synaptic and search for "flashplugin-nonfree"(you must have the "multiverse" repos enabled). If it is installed unistall it. If it isn't install it. After you do one of these, launch again firefox and test it on youtube and then tell us the results. If the problem persists after that then I might have another option for you.

---

### Post by MedellinManDem on 2008-06-25
> **SledgeHammer_999 said:**
> Go to synaptic and search for "flashplugin-nonfree"(you must have the "multiverse" repos enabled). If it is installed unistall it. If it isn't install it. After you do one of these, launch again firefox and test it on youtube and then tell us the results. If the problem persists after that then I might have another option for you.

Uninstalling it *seems* to have done the trick, although I will update if any other occurs. Thanks.

---

### Post by MedellinManDem on 2008-06-25
> **underground said:**
> I did the following and the problem dissapeared...goto synaptic,search for libflash and from the results remove anything is installed...hope it will help you..

I didn't do this, but thanks for your contribution anyway, it didn't go by ignored.

---

### Post by SledgeHammer_999 on 2008-06-26
> **MedellinManDem said:**
> Uninstalling it *seems* to have done the trick, although I will update if any other occurs. Thanks.

Ok I'm glad I helped for once!!!

---

### Post by MedellinManDem on 2008-07-02
This has started again, so I'm going to try "Underground's" initial contribution on page 1.

---

### Post by David Oxland on 2008-08-19
Thanks to the foregoers I did this
I uninstalled  flash and everything in Synaptic mentioning flash and disabled all the extensions in firefox.
After the new install  of Flash via Synaptic, Stumbleupon where I was opening wouldn't play videos. Installed Flashplayer via Synaptic and still wouldn't play.
Checked firefox errors and saw error mentioning JS.
Went to firefox addons and had two Java Console and JavaScript Options.
Enabled only Java Console and it plays.
Long and not sure why but It's reliable now.

---

