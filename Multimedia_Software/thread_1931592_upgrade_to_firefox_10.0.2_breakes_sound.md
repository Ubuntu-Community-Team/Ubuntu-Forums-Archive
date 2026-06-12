---
title: "upgrade to firefox 10.0.2 breakes sound?"
date: 2012-02-25
forum: Multimedia Software
---

### Post by Vonzap on 2012-02-25
Hello,

As a result of an upgrade to Firefox 10.0.2 I don't hear any sound neither using flash, (v. 11,1,102,62) nor HTML5 (flash uninstalled). Video plays OK. Sound in other programmes works fine, as well as in adobe plug-in Opera, so this might be Firefox-specific.

I am running Ubuntu 10.04.4 LTS and using OSS 4.2 (b 2004/201101102122). Any ideas how to fix this?

---

### Post by Yellow Pasque on 2012-02-26
Flash uses libasound for sound. I'm guessing you should emulate ALSA using the first method here: [http://www.opensound.com/wiki/index.php/Tips_And_Tricks#ALSA_Emulation](http://www.opensound.com/wiki/index.php/Tips_And_Tricks#ALSA_Emulation)

---

### Post by Vonzap on 2012-03-12
Sorry for the late reply. No, this method doesn't seem to have solved the problem. I'm guessing this is because Opera is communicating with flashplayer directly via operapluginwrapper-native. Firefox in its newer versions however uses plugin-container to communicate with flashplugin and other plugins (for security reasons I guess). That is why there were no problems with Firefox 9, only 10.X.

Is there a way around this?

---

### Post by lovinglinux on 2012-03-13
> **Vonzap said:**
> Sorry for the late reply. No, this method doesn't seem to have solved the problem. I'm guessing this is because Opera is communicating with flashplayer directly via operapluginwrapper-native. Firefox in its newer versions however uses plugin-container to communicate with flashplugin and other plugins (for security reasons I guess). That is why there were no problems with Firefox 9, only 10.X.

Is there a way around this?

Firefox uses plugin-container since version 3.6.

Try the fifth item on this list:

[http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions)

---

### Post by Vonzap on 2012-03-15
Thanks for your advice, but hmm... this is all very strange. Your method implements installation of PulseAudio, when everything used to be working well with OSS. (And still is, but I prefer Firefox to Opera). I haven't changed anything in configs, only upgraded to Firefox 10.0.2 via update-manager.

Firefox, differently than Opera launches flashplayer with -greomni options. Why? Maybe any other opinions?

---

### Post by lovinglinux on 2012-03-16
> **Vonzap said:**
> Thanks for your advice, but hmm... this is all very strange. Your method implements installation of PulseAudio, when everything used to be working well with OSS. (And still is, but I prefer Firefox to Opera). I haven't changed anything in configs, only upgraded to Firefox 10.0.2 via update-manager.

Firefox, differently than Opera launches flashplayer with -greomni options. Why? Maybe any other opinions?

Sorry, I messed the part that you are using OSS. Unfortunately, I can help you with that, since I was unsuccessful running OSS on my system. I tried it last week and got no sound too.

---

### Post by Vonzap on 2012-03-20
Just a few days ago a new set of updates to Firefox arrived, so now I am using Firefox 11.0. But no, this doesn't fix the problem as I was hoping for.
 
Maybe this should be a bug or smth.? Am I the only one having this problem?

---

