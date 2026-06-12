---
title: "atheros driver installed, but wireless doesnt work"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by li0id on 2009-01-28
well im having trouble getting my wireless card to work. i have a atheros card. ar242x 802.11 abg wireless pci express adapter (168c:001c). i'm running ubuntu 8,04. i installed the ndisgtk and used the net5211 driver. it says that it detects my driver. then when i unplug my wired connection to see if it works it won't, then also when i restart my computer and go back in to ubuntu, the ndisgtk (windows wireless drivers) says that the hardware for net5211 isnt present. when i run iwconfig while the hardware is present i get this:

```
michael@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```



then when i run iwconfig after i reboot and it says the hardware isnt present the wlan0 doesn't even show up.

 
can you please help, i've been at this for over a week non stop and can't figure it out. thanks in advanced

---

### Post by kevdog on 2009-01-28
I guess the ability to search on your version of the Ubuntu forums is broken:
[http://ubuntuforums.org/showthread.php?t=1052636](http://ubuntuforums.org/showthread.php?t=1052636)

---

### Post by li0id on 2009-01-28
i am running hardy not intrepid, so that way described in that thread isn't working. i did search the forums, and since i couldnt find anything that worked, i posted in the forums for help.

---

### Post by Ketara on 2009-01-28
Try this:

[http://ubuntuforums.org/showthread.php?t=766529&highlight=atheros+5007+madwifi](http://ubuntuforums.org/showthread.php?t=766529&highlight=atheros+5007+madwifi)

The howto is on page 1, although the link they post to get the madwifi file is old and broken. You'll have to go to the end of the thread to find the correct link.

That got my card working on Hardy, although I have since upgraded to Intrepid and it is broken again =)

---

### Post by kevdog on 2009-01-28
Here is also another link:
[http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

---

### Post by li0id on 2009-01-28
thanks for all the help. i followed the instructions on this page:

[http://it.dennyhalim.com/2008/08/atheros-5007-wifi-ar2425-chips-linux.html]("http://it.dennyhalim.com/2008/08/atheros-5007-wifi-ar2425-chips-linux.html")

and used r3933-20090127.tar.gz instead of the current due to that link being down. everything installed ok, no errors, i unpluged my connection to see if the wireless would work but it still does not then i restarted and still no go. when i run iwconfig i get this

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"laptop"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management min timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


am i missing something? is there something i need to type into the wireless network connection setup to make it work, because i don't know any keys or what security i have and also i just want to make it work so i can go to any wifi stop and get on the net without having to type any keys or encryptions in. im not even sure if id have to do that, just trying to cover all basis so you guys know what i'm trying to accomplish.

thanks in advanced.

---

### Post by li0id on 2009-01-28
bump

---

### Post by wower22 on 2009-01-28
> **li0id said:**
> thanks for all the help. i followed the instructions on this page:

[http://it.dennyhalim.com/2008/08/atheros-5007-wifi-ar2425-chips-linux.html]("http://it.dennyhalim.com/2008/08/atheros-5007-wifi-ar2425-chips-linux.html")

and used r3933-20090127.tar.gz instead of the current due to that link being down. everything installed ok, no errors, i unpluged my connection to see if the wireless would work but it still does not then i restarted and still no go. when i run iwconfig i get this

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"laptop"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management min timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


am i missing something? is there something i need to type into the wireless network connection setup to make it work, because i don't know any keys or what security i have and also i just want to make it work so i can go to any wifi stop and get on the net without having to type any keys or encryptions in. im not even sure if id have to do that, just trying to cover all basis so you guys know what i'm trying to accomplish.

thanks in advanced.

Im getting the same thing.

---

### Post by li0id on 2009-01-28
my wireless connection was working, than when i restarted, it doesn't work anymore. does anyone have any idea why this happens and how to fix it.

thanks in advanced

---

