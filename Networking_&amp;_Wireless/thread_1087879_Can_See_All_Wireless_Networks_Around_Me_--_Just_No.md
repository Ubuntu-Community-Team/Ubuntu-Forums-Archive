---
title: "Can See All Wireless Networks Around Me -- Just Not My Own (Ubuntu 8.10)"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by amj on 2009-03-05
Hi, 

I've reset my wireless router (Belkin F5D7230-4), changing it from WEP to WPA, now that I no longer have a WEP device.  The only problem is my laptop running Ubuntu 8.10 cannot see it. 

I have configured the router as WPA-PSK with TKIP.  

Three other devices can see & connect to the network:
 - Dell desktop (Windows Vista)
 - Lenovo T61 laptop (Windows Vista)
 - Mobile phone

The laptop with Ubuntu and the laptop with Vista are identical models with the same wireless adapter:

```
$ lspci | grep Wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

The Ubuntu laptop saw the wireless network fine when it was configured at WEP.  

The Ubuntu laptop sees other networks in the area, including a neighbors secured WPA-PSK network.

Any suggestions as to why the Ubuntu laptop as able to see other networks in the area, but not my own. (I am broadcasting the SSID).

Cheers, 
AJ

---

### Post by amj on 2009-03-05
Some further information:

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"belkin54g"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

$ 
```

"belkin54g" is the default name of the router.   I briefly connected to this after I reset the router.   I've since changed the name and set the security, and can no longer see the router ... even though 2 other PCs and 1 mobile phone can.   Is the wlan0 info about belkin54g somehow blocking me from seeing the router, perhaps?  

Cheers, 
AJ

---

### Post by zenithdave on 2009-03-05
Im having exactly the same problem with the same router !!

[http://ubuntuforums.org/showthread.php?t=1087088](http://ubuntuforums.org/showthread.php?t=1087088)

Could you try rebooting the router and computer at the same time, this gets my wireless working for some strange reason .

---

### Post by amj on 2009-03-05
Hi, 

I hadn't tried shutting off the router -- had done lots of laptop shutdowns with no effect -- so I gave it a go. 
Unfortunately, I'm still not seeing my own router. 

It's not a signal strength issue.  My Ubuntu laptop is 3 feet from the router.   The Vista laptop is 4 feet away. 

I just had the Vista laptop do a network rescan.   It found 3 networks:
 - belkin54g (but a weak signal, so it must be a non-immediate neighbor)
 - the neighbor's router with wpa-psk
 - my router with wpa-psk
But my Ubuntu laptop still just sees the first 2. 

Any suggestions on how to clear "belkin54g" from my iwconfig listing, or does that just happen, since it's an open network?

Cheers, 
AJ

---

### Post by juroen on 2009-03-05
its not really an apply for the topic (sorry for that)

but which software do you use for scanning for the network?

Thanks

---

### Post by Herter on 2009-03-05
I'm having the exact same problem..!

Wireless works fine in windows, but on Ubuntu I can see 4-5 other nets, just not my own!.. :(

---

### Post by amj on 2009-03-05
> **juroen said:**
> which software do you use for scanning for the network?

The standard app with Ubuntu 8.10:  NetworkManager Applet 0.7.0

---

### Post by amj on 2009-03-05
Another device that can see and and connect to my router with WPA-PSK/TKIP:
 - our Xbox 360

---

### Post by zenithdave on 2009-03-05
Very non technical but after a few concurrent reboots of the laptop and router the the wireless connects every time i try now (without router reboot)!!! crazy 

AMJ, have another go rebooting the router and try booting the laptop up first then the router, it seems to toggle something when you do it enough times and when its flicked over it stays there.

I also observed the computer will not shut down properly when the fault is happening !!!!!!

---

### Post by amj on 2009-03-05
ok ... i'll do a few shutdowns, and see what happens ... back soon ...

Update:  nope ... three reboots of the router and laptop, and I'm still not seeing my network from my Ubuntu laptop.

---

### Post by amj on 2009-03-05
Is there a file that stores previously found networks?
Since the MAC address of the router has not changed, but the security has, maybe there's some file on my laptop causing confusion. 

To test the idea, I'm going to find my LiveCD, and see if I can see my network when booting off that.

---

### Post by zenithdave on 2009-03-05
Damn !! :(

This is so weird.

Help!!!

Worth a try amj, im very confused by the fault and the cure that i use.

---

### Post by amj on 2009-03-05
> **amj said:**
> Is there a file that stores previously found networks?
Since the MAC address of the router has not changed, but the security has, maybe there's some file on my laptop causing confusion. 

To test the idea, I'm going to find my LiveCD, and see if I can see my network when booting off that.

No joy with the Ubuntu 8.10 CD, but I found my network with Linux Mint (Elyssa), and I'm submitting post while running Mint.  I'm going to try the Ubuntu 8.04.1 CD, and see what other LiveCDs I have.   I'll list my results.

---

### Post by zenithdave on 2009-03-05
> **amj said:**
> I found my network with Linux Mint (Elyssa)I'll list my results.

:guitar:

Funny old world.I did not get Mint to work no matter what i did.

Glad something is starting to work for you :D

---

### Post by amj on 2009-03-05
> **amj said:**
> No joy with the Ubuntu 8.10 CD, but I found my network with Linux Mint (Elyssa)

Ubuntu 8.04.1 Live CD found my network as well ... I'm posting this while running that LiveCD.  

The wireless applet is "nm-applet 0.6.6"

Weird that an older version of Ubuntu works better ...

---

### Post by deadmanmss on 2009-03-05
hi i also am having the same problem, i can pick up other wireless signals and connect to them but not the one i want to connect to

---

### Post by deadmanmss on 2009-03-05
> **amj said:**
> Ubuntu 8.04.1 Live CD found my network as well ... I'm posting this while running that LiveCD.  

The wireless applet is "nm-applet 0.6.6"

Weird that an older version of Ubuntu works better ...


yea i previously was running 8.04 and i could find that network on it but since getting the new 8.10, i that particular signal is not getting picked up, but i can pick it up on other laptops (vista, xp)

---

### Post by paintball9 on 2009-03-05
i had some simillar issues with a router but it was on a windows machine, you might want to try not using tkip, i dont remember what the alternative was (aes maybe) but that was what fixed it for me on the windows machine, i think some wireless cards have problems when using certain types of encryption.

---

### Post by amj on 2009-03-06
I've just booted up with Mint 6 (Felicia), which is based on Ubuntu 8.10, and also uses NetworkManager 0.7.0.   Mint 6 couldn't find my network either.

Something I noticed one Ubuntu 8.04.1 and Mint 5 (Elyssa) ... when it found the network and asked me to enter the security code, if I left one of the pull-downs on "Auto", it wouldn't connect, but if I manually set it to "TKIP" it worked.  
In line with paintball9's suggestion, it made me think of trying the alternative to TKIP -- AES.

I'll reconfigure my router and report back later.

---

### Post by amj on 2009-03-06
Success!

First I tried switching from TKIP to AES, but I still couldn't connect. 

I remembered that when I went from WEP to WPA, I also changed the channel from 7 to 12 (to move away from a neighbor's channel).  So, I set the channel back to 7, and was able to see my router (still on AES). 

Then, I switched to TKIP (staying on channel 7), and I could find the network again.  

As one extra step, I booted Mint 6 again, and this time it found my router as well. 

So, it appears the issue with Ubuntu 8.10 / NetworkManager Applet 0.7.0 is associated with the channel number.  If I get a chance later, I might try running through all the channels, and see if there is a pattern.

So, for those of you with the same issue, can you report the channel your router is currently using, try switching to a different one, and report back on your results?

Cheers, 
AJ

---

### Post by amj on 2009-03-06
I've worked through all the channels on my router:
 - Connected fine on channels 1 - 11
 - No connection on channels 12 & 13

Hopefully this helps others with connection issues.

---

### Post by Yashiro on 2009-03-06
> i had some simillar issues with a router but it was on a windows machine, you might want to try not using tkip, i dont remember what the alternative was (aes maybe) but that was what fixed it for me on the windows machine, i think some wireless cards have problems when using certain types of encryption.
If you're using WPA2 you should try to use AES/CCMP. TKIP was a transitionary WPA standard.
WPA2/TKIP implementation should be more sketchy than WPA2/AES, not the other way around.

---

### Post by amj on 2009-03-06
> **Yashiro said:**
> If you're using WPA2 you should try to use AES/CCMP. TKIP was a transitionary WPA standard.
WPA2/TKIP implementation should be more sketchy than WPA2/AES, not the other way around.

Thanks for the info.  I'll look into switching over to AES.  But AES didn't work on channel 12 for me either (which is where my problems started).   It seems my connection problem was channel-related rather than AES vs TKIP.

*Update:* After a quick read on TKIP v AES, I've followed your advice and switched the network to AES.  Thanks.

---

### Post by detroit/zero on 2009-03-06
Sorry to chime in late.. I guess I could have helped more if I got here sooner.

You asked about a file that stores network settings: I don't know where the actual file is located, but if you right-click on the nm-applet icon and select Edit Wireless Networks, it brings up all the info for networks you have saved over time.

There, you could have removed or edited the information for your router before you made the changes (including the channel it was set to, encryption type, etc).

If you first change all the security settings in your router to what you want (WPA, TKIP, channel, whatever else..) the go into Edit Wireless Networks and delete the entry, you should be able to find and select the new network name, enter the passcode, and connect like normal.

---

### Post by Reiger on 2009-03-06
I've had the same problem with a different router. What I did was the following:
[list="1"]
[*]Grab an ethernet cable, plug one end into the laptop the other into an ethernet port on the router, if not done automatically already: connect using the wired interface.
[*]Log into the router's admin control panel (for me it was [http://192.168.2.1/](http://192.168.2.1/) I have another router for which it is [http://192.168.1.1/](http://192.168.1.1/))
[*]Change the ESSID of the network to something new.
[*]Restart the router so the changes take into effect
[*]Disconnect the laptop
[*]Refresh the list of wireless networks found by network manager.
[*]Connect to the new ESSID.
[/list]

---

### Post by amj on 2009-03-06
Hi Reiger, 

Thanks for the suggestion.   I didn't mention it in my posts, but I had changed the SSID as well, much in the way of your procedure, but for me, it made no difference. 

I've found it very repeatable for my connection that it's down to using channels 1-11 versus 12-13. 
 
Soon after my observation of this, I had a conversation with a friend (who is quite RF knowledgeable), who indicated he's come across problems on other PCs connecting to channel 12. 

Cheers, 
AJ

---

### Post by zenithdave on 2009-03-06
Glad you got it working AMJ :D and helped many in the process.

My router is set to auto channel and is currently using channel 1 and is working fine.

I should imagine my wild rebooting eventually selected a good channel.

Great stuff :D

---

### Post by zenithdave on 2009-03-06
I can 100% confirm i cannot see my wireless when the router is set to channel 12 change it back to 1 and it works very well.

Great work AMJ :KS

A follow up read

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275279](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275279)

---

### Post by amj on 2009-03-06
Z-D, 

Thanks for checking channel 12 and confirming it doesn't work for you either. 

And thanks for the link.   I ran the iwlist command shown in one of the posts there, and indeed, I'm only seeing channels 1-11 in the 2.4 GHz band (plus a bunch in the 5 GHz band). 

The info in that link showing how to change the region to EU confirms my suspicion that my laptop was being limited to US bands.   Excellent further digging, Z-D!

Cheers, 
AJ

---

### Post by zenithdave on 2009-03-06
This is a great day, the sole reason i have done so many Ubuntu install's was because of this problem, i have been at it for months now and its fixed woohoo.

I had no other issues with Ubuntu ever :D

Ubuntu rules :D

This really needs to be pinned somewhere???

Cheers AMJ have a great weekend.

---

### Post by Herter on 2009-03-06
Hi

I've also solved my problem by changing the channel to 1.. it was set on auto and I guess it happened to choose 12 or 13 then..

Anyway, it works fine now :)  finally!   

THANKS to amj - the king of kings!

---

### Post by amj on 2009-03-07
king of kings?   I'm humbled!  I'll tell my wife about my new title, but I'm sure she'll have her own opinion on that.  ;)

Anyway, back to wifi, I tried the suggestion from zenithdave's link, and "$ iwlist wlan0 channel" now shows channels 12 & 13.  I haven't tested linking to channel 12 or 13 (the kids are in an network game on the xbox right now, and purposely dropping the link would initiate an assault on the throne!), but I'm reasonably confident they'll work now.

Good teamwork and help all around here.   I think I have to share the crown with all of you!

---

### Post by zenithdave on 2009-03-07
You might want to mark this thread as solved amj might help to draw more people in from the post titles :D

---

### Post by ugm6hr on 2009-03-07
Sorry I didn't see this earlier...

This is a known "bug" for European and Japanese users of Intel wifi chipsets:
[http://www.ubuntu.com/getubuntu/releasenotes/810#Only%20US%20wireless%20channels%20enabled%20by%20default%20on%20Intel%203945](http://www.ubuntu.com/getubuntu/releasenotes/810#Only%20US%20wireless%20channels%20enabled%20by%20default%20on%20Intel%203945)

---

### Post by amj on 2009-03-07
> **zenithdave said:**
> You might want to mark this thread as solved amj might help to draw more people in from the post titles :D

I tried to do that, but it didn't work.   Is there a link to the proper procedure for doing so?

---

### Post by zenithdave on 2009-03-07
Click on thread tools (red writing) ;)

---

### Post by amj on 2009-03-07
> **zenithdave said:**
> Click on thread tools (red writing) ;)

The options I see under Thread Tools are:
 - Show Printable Version
 - Email This Page
 - Subscribe to this Thread
 - Add a Poll to this Thread

But nothing like "mark solved"   :confused:

---

### Post by ugm6hr on 2009-03-07
> **amj said:**
> But nothing like "mark solved"   :confused:

Due to database issues, that feature was disabled.

I recommend adding "solved" as a tag instead (already done).

---

### Post by zenithdave on 2009-03-07
** note to self, read release notes :(

'The iwl3945 wireless driver defaults to the US regulatory domain for wireless, so wireless networks on channels forbidden by US regulations but permitted by European or Japanese regulations will not work out of the box. This affects IEEE 802.11b/g channels 12 (Europe and Japan), 13 (Europe and Japan), and 14 (Japan only), as well as all 802.11a channels. (Some other wireless drivers may be affected; this is the only one we are sure of so far.) '

Its not really hardware specific though is it, just regional default setups? 

Is it illegal to enable those channels in Ubuntu ? like restricted closed drivers or did no one really think about us Europeans ;)

---

### Post by ugm6hr on 2009-03-07
> **zenithdave said:**
> Is it illegal to enable those channels in Ubuntu ? like restricted closed drivers or did no one really think about us Europeans ;)

I think the Intel developers just thought that the world ended at the Atlantic Ocean ;)

No harm meant; Europeans believed that once too!

---

