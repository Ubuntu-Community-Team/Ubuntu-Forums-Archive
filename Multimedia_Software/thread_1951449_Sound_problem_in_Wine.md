---
title: "Sound problem in Wine"
date: 2012-04-02
forum: Multimedia Software
---

### Post by Azyx on 2012-04-02
I have problems with Spotify under Wine 1.2 and 10.04LTS. I find a solution to the problem with 'winetricks winhttp' on my newer 11.10 machine, but there was no winetricks on the old 10.04LST and wine 1.2.

But before I find the problem, I unchecked the ALSA-driver under Wine-configuration (As an old how-to showed that, but it did not help). Then I add PPA for wine och lucid, and made an upgrade and run 'winetricks winhttp'. Now I don't have any sound, and under Configure Wine-->Audio, there are not any chois to change sounddriver, It just says: Selected driver: wineoss.drv
And I don't get any sound when I press 'Test sound'.

So. How can I select sound driver from wineoss.drv to ALSA in Wine 1.3?

---

### Post by Azyx on 2012-04-02
> **Azyx said:**
> I have problems with Spotify under Wine 1.2 and 10.04LTS. I find a solution to the problem with 'winetricks winhttp' on my newer 11.10 machine, but there was no winetricks on the old 10.04LST and wine 1.2.

But before I find the problem, I unchecked the ALSA-driver under Wine-configuration (As an old how-to showed that, but it did not help). Then I add PPA for wine och lucid, and made an upgrade and run 'winetricks winhttp'. Now I don't have any sound, and under Configure Wine-->Audio, there are not any chois to change sounddriver, It just says: Selected driver: wineoss.drv
And I don't get any sound when I press 'Test sound'.

So. How can I select sound driver from wineoss.drv to ALSA in Wine 1.3?

Find a hint to solution here:
[http://wiki.winehq.org/Sound](http://wiki.winehq.org/Sound)

I open regedit.exe and followed the HKEY-link (puh I sweating and remember the windows time (; ) and find the name,value,string or whatever in the field Audio  'oss'. I tried to change it to 'alsa'  and it worked :)

---

