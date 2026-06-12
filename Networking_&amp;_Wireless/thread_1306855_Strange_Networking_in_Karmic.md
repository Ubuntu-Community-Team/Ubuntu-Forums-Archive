---
title: "Strange Networking in Karmic"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2009-10-30
As a continuation of the now closed thread ([http://ubuntuforums.org/showthread.php?t=1300774](http://ubuntuforums.org/showthread.php?t=1300774)) dealing with the seemingly random networking issues in Karmic, just wondering if anyone else can confirm some wireless networking problems.

I'm running an Atheros chipset and using ath5k for wireless on a Lenovo z61e, as well as having rid myself of network-manager (pos) and wicd I just use direct definitions in /etc/network/interfaces and /etc/wpa_supplicant.conf. In short, when I *first* login and start-up any browser, things move fine for a few minutes, but quickly goes incredibly slow. If I wait about five minutes, everything seems to return back to normal. I'm wondering if there's an ipv6 setting I'm missing or something similar. I've already done all the "tricks" about getting things to work; e.g., editing /etc/nsswitch.conf and /etc/resolv.conf.

Any other ideas?

---

### Post by spotrick on 2009-10-30
I can confirm there's a problem with wireless. My symptoms match yours exactly, although my wifi setup is very simple.

I note that the wireless connection to router is fine -- it connects OK and stays connected. It's the connecting to the web through the wireless router that seems a problem.

Also, I notice that ping seems fine. It's only more sophisticated connections that fail.

---

### Post by Eric Lathrop on 2009-10-30
I just did a clean install to 9.10 from 8.10, and I am having the same issues.
I have an Atheros AR5001X+. It's connected to the AP pretty solid, but we pages won't load consistently, and I keep getting connection reset. I used to run the card under madwifi with no problems should I switch back?

---

### Post by x2wdtoyotax on 2009-10-31
Yeah me too. I also have an Atheros Chipset on my wireless card. Super slow speeds all around.

---

### Post by vkov_tinsky on 2009-10-31
Same problem here (Netgear WG311T via ath5k on 9.10):
Initial download speed as expected, after a minute or so:
a) speed goes down to zero
b) cannot ping router(gateway&dns), can still ping other PCs on local network
c) ~30-90 seconds later downloads resume but speed drops (to zero) again after around a minute

The above repeats indefinitely. (No problems with router etc. with other OSs on same PC)

Only installed 9.10 yesterday so haven't tried madwifi yet. This problem makes installing/upgrading large packages almost impossible since the download frequently times out (luckily the partial apt downloads are resumed).

---

### Post by moore.bryan on 2009-10-31
AKAIK, this is "normal" behavior for 9.10 right now... I don't know if there's any particular "fix" planned, but I know there are *a lot* of us in the same boat...

---

### Post by moore.bryan on 2009-11-01
Hmm... I'm beginning to wonder if this could be an Avahi issue... any ideas?

---

### Post by aimaaditya on 2009-11-01
i have been using ubuntu for 1 and half year now after i got fed up with vista... i joined this forum because i having this trouble ever since my coll decided to go with MAC filtering with access points...i am able to connect with dual booted win7 on the same system as well as with karmic on wep enabled access points..but not on MAC filtered ones...i am able to connect using Win 7 though.....

---

### Post by lokutus25 on 2009-11-02
My situation is eeePC 1101HA with a fresh install of Karmic. The WiFi Adapter is Atheros AR9285 and my problem is the same as yours...very slow network speed.
I read about an IPV6 problem...is there a useful thread?

---

### Post by moore.bryan on 2009-11-02
> **lokutus25 said:**
> My situation is eeePC 1101HA with a fresh install of Karmic. The WiFi Adapter is Atheros AR9285 and my problem is the same as yours...very slow network speed.
I read about an IPV6 problem...is there a useful thread?
For disabling ipv6? Only a million... ;-) A quick search will turn up lots for you.

It would seem by my discussion in other threads it is still related to a dns issue, even though that doesn't *seem* to be my problem.

---

### Post by moore.bryan on 2009-11-05
Let me add to this mix even more... playing around with Wireshark showed me a lot of MDNS queries. Made me wonder something about the /etc/nsswitch.conf file, so I "man-ed" it. The [man page]("http://linux.die.net/man/5/nsswitch.conf") shows a different order from things on the host line in the generic Karmic file. 

My original nsswitch.conf has this line:
```

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

```The nsswitch.conf man page seems to say the "files" entry should happen **after** dns, like this:
```

hosts: files dns [!UNAVAIL=return]

```This *seems* to be a mix of the "original" nsswitch.conf "fix" of deleting the mdns4_minimal and mdns4 information and ordering.

I made this change and am testing response times; things seem to be resolving more quickly and I haven't, yet, had my connection go "dead." Perhaps a few more could try this one out and let me know? I'm also going to post this in the other threads to which I'm subscribed about similar networking issues. All together, we've got to come up with something!

---

### Post by moore.bryan on 2009-11-14
My "fix" above did nothing for me, as it turns-out. I am now, though, somewhat convinced it is a WPA issue because after some recent updates my WEP connection is fine, but my WPA-PSK still drops shortly after connection. It *eventually *becomes responsive again and it just as speedy as ever, but that "dead zone" is unacceptable. How is this something which hasn't received my attention? WEP is a *poor* choice for security, so (some rhetorical questions) why *in the world* would anyone ever use it with WPA as a solution and, in theory, if everyone's "supposed" to be using WPA how would *this* kind of networking problem not be solved in nanoseconds?

Could someone point me to a* good* step-by-step, in-depth guide for WPA files, programs, and scripts Ubuntu uses; I'd like to start digging into the "meat and potatoes" and get this solved.

This seems to be almost 100% WPA related. Anyone?

---

### Post by moore.bryan on 2009-11-14
Perhaps a new wrinkle: Wifi Protected Setup (WPS) in not supported in **any** Ubuntu flavor, as per [here]("https://bugs.launchpad.net/ubuntu/+bug/388553"), but my wpa_supplicant *seems* to be trying to use it. After a regular drop in network activity I fired-up Wireshark, saw nothing; double-checked iwconfig, saw nothing; randomly checked the /var/log/syslog file and, wait a second...
```

Nov 14 15:48:13 localhost wpa_supplicant[1080]: WPS-TIMEOUT Requested operation timed out
```
Any ideas guys?

---

### Post by moore.bryan on 2009-11-16
This is F-KING ridiculous! My network connection is dropping-out every thirty-seconds tonight. How in the hell is this not more important? I've scoured the 'net and these fora and others have the problem too!

---

### Post by cygnis1 on 2009-11-16
I just had some problems with my wireless. It had been working with Karmic just fine, then tonight it connected and then disconnected and I couldn't get it to work.  I have a Dell xps 1330, running Karmic.  Connected with the ethernet cable and began my search through the forums.  I know this is not a very geeky solution, but was chatting with my brother and he told me he had the same problem with Vista.  Seems there is a switch on the outside of the laptop for wireless.  I guess I must of turned off wifi.  I switched it back on and now wifi is working.  I hope this helps someone.

---

### Post by xtbt on 2009-11-19
> **cygnis1 said:**
> I just had some problems with my wireless. It had been working with Karmic just fine, then tonight it connected and then disconnected and I couldn't get it to work.  I have a Dell xps 1330, running Karmic.  Connected with the ethernet cable and began my search through the forums.  I know this is not a very geeky solution, but was chatting with my brother and he told me he had the same problem with Vista.  Seems there is a switch on the outside of the laptop for wireless.  I guess I must of turned off wifi.  I switched it back on and now wifi is working.  I hope this helps someone.

I don't think that the case of 'moore.bryan' or 'lokutus25' and (unfortunately) me.

The situation in my case is like this:

- I was using Ubuntu 8.10 x64 some months ago, and everything was just fine with wireless, using madwifi. I was using a ACER 4520 laptop with Atheros adapter. I then give this laptop to my wife and I got another one.

- This other laptop is a ACER 5536 with an atheros adapter too. I did a fresh install of Win7 x64 and everything was just fine (even wireless, works perfect). I then made a fresh install of Ubuntu 9.10 (Karmic) x64 and I was surprissed because my wireless was detected since the first time I logged on.

- I started to install packages, update ubuntu, download stuff, configuring it but sometimes I noticed that something was wrong with my wireless connection. I then started to give my attention to this issue, and started to search for solutions or workarounds, and surprissingly there was a lot of people like me suffering with this problem (Speed drops, crazy signal strenght, suddenly disconnections, etc, etc.).

*NOTE: I had by this time 2 AP's using WEP.

- As suggested by some other member of this glorious forum, I changed both of my AP's from WEP to WPA (dsl) and WPA2 (cable). I then started to make some tests on both.

- Also, as suggested by some other member, I replace Network Manager with WICD. No difference though, it didn't help in any way. I like WICD's interface. So I keep it.

- Aparently, the WPA(dsl) AP problem dissapear. I can stay connected all day, no speed drops, no crazy signal strenght, no nothing. Not a single issue. BUT (there's always a but), I have to be less than 30 mts away from the AP if I want to keep the peace between my adapter and the AP ... some more meters and I get the same crazy behaviour as before.

- On the other side, the WPA2(cable) AP problem is still there, even if I'm 1 meter away from it.

*CONCLUSION:
   I'll need to change my WPA2(cable) AP to WPA, and see if it stays connected like it has to. When I get some results I'm gonna post them here, maybe I can help some lost souls out there.

*FINAL NOTE: The problem doesn't reside in my wireless adapter because I don't have any kind of problem using windows 7.

Like I always say, I'm not making any comparison between win7 and Ubuntu. I prefer Ubuntu over any version of windows, but the facts are the facts, and the fact my friends is that a lot of people are having problems with their Atheros wireless adapter ... the sad thing is that Ubuntu developers doesn't seem interested in fixing it (sorry if I hurt someones feeling).

Tonight I'll post my results.

---

### Post by moore.bryan on 2009-11-19
> **xtbt said:**
> I don't think that the case of 'moore.bryan' or 'lokutus25' and (unfortunately) me.
True... I don't even have access to Windows at all; straight Linux.
> **xtbt said:**
> - Aparently, the WPA(dsl) AP problem dissapear. I can stay connected all day, no speed drops, no crazy signal strenght, no nothing. Not a single issue. BUT (there's always a but), I have to be less than 30 mts away from the AP if I want to keep the peace between my adapter and the AP ... some more meters and I get the same crazy behaviour as before.

- On the other side, the WPA2(cable) AP problem is still there, even if I'm 1 meter away from it.
Hmm... this almost certainly confirms my hypothesis the trouble resides in WPA, particularly wpa_supplicant. It *is* strange, though, it is affecting WPA2 and not WPA.

Please do report back with any additional info you can gather, xtbt.

---

### Post by xtbt on 2009-11-20
Well, I just changed my second AP from WPA2-PSK to WPA-PSK, I'm using win7 right now as I type, and curiously, just after I changed it to WPA, the speed went notably up (I don't really know why. That's what I like about computers, there's something new to learn everyday).

*UPDATE: I tested my 2Wire (dsl) AP; which has WAP and now works good if I'm near, connecting to it from a distance of almost 30 meters and it worked ok for 1 hour (more than before when it has WEP) and then suddenly got disconnected ... no wireless networks found anymore. Only solution, restart. So, definitely, I have to be near to work with that AP, period.

Right now, like I wrote before, I'm posting this using Win7. I'm gonna restart computer, log into Ubuntu, and test my second AP (which I just changed it from WPA2 to WPA). This is a Cable Modem AP, Netgear CG814GCMR. I'm 10 meters away from it so it has to work just fine.

I'll post my results like in 30 minutes.
X-TBT a.k.a. The Mentor.

---

### Post by xtbt on 2009-11-20
> **xtbt said:**
> Well, I just changed my second AP from WPA2-PSK to WPA-PSK, I'm using win7 right now as I type, and curiously, just after I changed it to WPA, the speed went notably up (I don't really know why. That's what I like about computers, there's something new to learn everyday).

*UPDATE: I tested my 2Wire (dsl) AP; which has WAP and now works good if I'm near, connecting to it from a distance of almost 30 meters and it worked ok for 1 hour (more than before when it has WEP) and then suddenly got disconnected ... no wireless networks found anymore. Only solution, restart. So, definitely, I have to be near to work with that AP, period.

Right now, like I wrote before, I'm posting this using Win7. I'm gonna restart computer, log into Ubuntu, and test my second AP (which I just changed it from WPA2 to WPA). This is a Cable Modem AP, Netgear CG814GCMR. I'm 10 meters away from it so it has to work just fine.

I'll post my results like in 30 minutes.
X-TBT a.k.a. The Mentor.

The results are not satisfactory. I was using my cable modem AP just fine, nice speed, the signal strength was variable, 10 meters away. The connection was alive for like 40 minutes and then suddenly died.

FINAL CONCLUSION:
   I'm not happy at all with the results. I'll definitely have to take another path. Another thing is that when I run dmesg in terminal, there are a lot of error messages regarding my wireless driver (ath9k in my case). So my bet is that no matter what I do, what I change, what I test, there won't be any 100% solution.

   At least in my case. The only thing I can do now is un-installing all ath drivers and installing the madwifi wireless drivers that I used to use back in intrepid days.

I'll not make any further tests regarding wireless AP configuration, but if things get fixed with Madwifi, I'll post my results right here just to let you know.

Until then,
X-TBT a.k.a. The Mentor.

---

### Post by moore.bryan on 2009-11-20
Could you post the ath9k errors? Although I'm using the ath5k one, perhaps it could lead down an unexpected path...

---

### Post by dca on 2009-11-20
Has anyone tried on a clean 9.10 install using 'ndiswrapper'?  Try blacklisting the ath5k & ath9k drivers or whatever from loading @ start-up and use that (ndiswrapper) w/ Windows driver & nm-applet?
 
The only reason I say, I had an Acer 5610z laptop that came with the brand spanking new Ambit PCIx card running an Atheros chipset that as each kernel was released would identify itself as something different.  Ath5k came out and it auto-recognized & config, however, it would exhibit the same things being described.  The only work-arounds at the time (you can probably scan for my threads from years back) was either a hotfix-patch from MadWifi (prior to ath*k kernel drivers) or using ndiswrapper & Windows drivers.

---

### Post by moore.bryan on 2009-11-20
I used the ath5k driver under Jaunty without issue; do you still think your comment could be relevant?

---

### Post by xtbt on 2009-11-20
Well ... considering all the problems I had with this ath*k drivers, I'm now trying to install Madwifi drivers on Karmic. Unfortunately I can't get them to work well. I've already blacklisted ath*k drivers but my wireless adapter doesn't came up on startup.

I'm working on it right now, if I get to a solution or something I'll immediately post it right here.

About the ath*k errors, they said something like 'Unable to wake up ...' or something like that. Let me try to fix this madwifi thing and then I revert changes to see the error again.

C-ya later,
X-TBT a.k.a. The Mentor.

---

### Post by dca on 2009-11-20
> **moore.bryan said:**
> I used the ath5k driver under Jaunty without issue; do you still think your comment could be relevant?

Got me on that one...  the issues I had date back to this post:
 
[http://ubuntuforums.org/showthread.php?t=789824](http://ubuntuforums.org/showthread.php?t=789824)
 
...It was the same on all distro(s) I tried:  Ubuntu, Fedora, & openSUSE.  If it can be confirmed as a kernel driver regression than ndiswrapper may be only hope.  Haven't had the laptop with the Atheros since last year so it makes it difficult.

---

### Post by dca on 2009-11-20
I got rid of laptop around when 8.10 cam out and it seemed to recognize it fine but the biggest thing was when it finally got running okay with ath5k (may be confusing when using Fedora) the wireless connection would just "DROP" for no reason, no interface restart at CLI would do it, had to reboot laptop and pray it stayed connected for couple more hours.  Kicked out ath*k again and went back to ndiswrapper and driver CD from Acer...
 
At least with mine, it was guaranteed that the new ath*k drivers was still infant and stunk requiring that fix in the post I showed you or ndiswrapper.
 
In this case, now that ath*k is 'a little more mature' we've added extra variables.  Is the driver fist fighting with wpasupplicant or is ath*k not compatible now with any GUI network controller, or is it a legitimate kernel driver regression...

---

### Post by xtbt on 2009-11-20
> **dca said:**
> Got me on that one...  the issues I had date back to this post:
 
[http://ubuntuforums.org/showthread.php?t=789824](http://ubuntuforums.org/showthread.php?t=789824)
 
...It was the same on all distro(s) I tried:  Ubuntu, Fedora, & openSUSE.  If it can be confirmed as a kernel driver regression than ndiswrapper may be only hope.  Haven't had the laptop with the Atheros since last year so it makes it difficult.

I know what you mean 'dca'. In a matter of fact, I'm trying to make madwifi works with no success. I've already blacklisted any reference to ath*k and put to load ath_pci in /etc/modules but apparently the wifi adapter refuses to turn on (I can tell by the color of the light on the wireless button on the laptop).

I'll make further tests and see if I can get up on something.

---

### Post by dca on 2009-11-20
I know, incredible, two Atheros issues on same page in wireless/networking support...
 
[http://ubuntuforums.org/showthread.php?t=1286503](http://ubuntuforums.org/showthread.php?t=1286503)
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)
 
Last ones a how-to use MadWifi in Kubuntu which should apply to Ubuntu.  More and more (thank God I don't have the card anymore, no offense guys) I see, they're calling it kernel regressions with ath*k drivers...

---

### Post by bkratz on 2009-11-20
[QUOTE=dca;8355531]Has anyone tried on a clean 9.10 install using 'ndiswrapper'?  Try blacklisting the ath5k & ath9k drivers or whatever from loading @ start-up and use that (ndiswrapper) w/ Windows driver & nm-applet?
/QUOTE]



Please see this bug listing regarding ndiswrapper.

[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716)

---

### Post by moore.bryan on 2009-11-20
Interesting twist: I've switched my router to WPA-PSK (TKIP) instead of WPA2-PSK (AES) and things *seem* to be acting "normal." I'm going to put my network under some heavy stress over the next few hours and report back findings.

I'm also in an email conversation with some of the wpa_supplicant devs; I'll report back on any info I can get out of that.

---

### Post by xtbt on 2009-11-20
> **moore.bryan said:**
> Interesting twist: I've switched my router to WPA-PSK (TKIP) instead of WPA2-PSK (AES) and things *seem* to be acting "normal." I'm going to put my network under some heavy stress over the next few hours and report back findings.

I'm also in an email conversation with some of the wpa_supplicant devs; I'll report back on any info I can get out of that.

That was what I deduced with one of my AP's, which is a 2Wire. That's very strange but still, this is getting me nuts. I'm playing with madwifi with no satisfactory results. I'm gonna go back to Network-Manager and take off Wicd and see if I can fix this.

---

### Post by moore.bryan on 2009-11-20
It's still somewhat intermittent, but better. This *has* to be a wpa_supplicant issue because my work uses WEP and that's fine. I'd switch to that, but have read **far** too much about the WEP security issues.

---

### Post by harvestall on 2009-11-20
Just like everyone else, my Ubuntu 9.10 internet has suddenly became very unstable. It worked fine for a week and a half and then out of the blue,  it got crazy.  I finally figured out something that works for me.  It might work for you too.

Here's the wireless card I'm using:
Realtek RTL8187B Wireless 802.11g 54Mbps Network Adapter

So what I did was manually set my DNS server settings.  Using Wicd, I went into:

 Preferences > General Settings
 
I checked the box 'Use global DNS servers.'  Then I manually put in the DNS servers as they were listed in my wireless router.  Under External Programs Tab, everything is set to Automatic.  Under Advanced Settings, my WPA Supplicant Driver is wext and my Backend is set to external.

Then, I went back and refreshed the local networks.  I went into the properties for the network I'm connecting to.  'Use Static DNS' is checked.  'Use global DNS servers' is checked.  'Use Encryption' is checked and I have my network password entered.

Once I did this and connected, everything started working perfectly.  I hope it keeps working.  If you're at the end of your rope you might give it a try.

---

Specifically what my internet was doing:

I could ping, wget, download ubuntu updates, and use the sofware center, but I couldn't use my browser.  I tried firefox and seamonkey - both wouldn't work.  Some websites would occasionally work.  It seems like I could always go to getbrushes.com, but I could never make it to facebook, hotmail, or google.  The browser would just keep trying to connect or transfer data but would never finish.

---

### Post by xtbt on 2009-11-20
Unfortunately, this is not my case. My problem is very different. I can do everything that has to do with the internet but suddenly gets disconnected.

I was playing all day with madwifi with no success. I think this is not my path to follow. I'm gonna give compat-drivers a shot and then I'll post the results.

Until then,
X-TBT a.k.a. The Mentor.

---

### Post by xtbt on 2009-11-21
[IMPORTANT UPDATE]
Well people, I'm very exited because I think I finally [SOLVE] my wireless problem under Ubuntu.

After doing several things, from changing the encryption scheme of both of my AP's, to blacklisting the ath*k drivers originally installed and installing Madwifi, I lead to a thread that gave me the solution.

I'm going to divide the post in four parts, my equipment, the initial problem, everything I did to try to fix it, and the final solution.

[B]<EQUIPMENT>
[/B]   Laptop: ACER ASPIRE 5536
   Wireless Adapter: Atheros AR928X
   Wireless AP 1: 2Wire HT-2701 (DSL Wireless Router)
   Wireless AP 2: Netgear CG814GCMR (Cable Wireless Router)
[B]
<INITIAL PROBLEM>[/B]
   Everything started since I fresh-installed Ubuntu 9.10 x64 in my laptop (After fresh-installing Win7).
*NOTE1: Both of my AP's had WEP (I was too lazy to change the default).
*NOTE2: No problems at all with Win7 when I was configuring it/installing the software, updating it, downloading things, watching youtube, etc, etc.
   Since the first boot into Ubuntu, I started to notice some strange behaviour with my wireless connections, the signal went crazy sometimes going down from 85% to 10% with no reason, and then going back to 80%, and after an hour or so it suddenly disconnected ... no matter how far I was from the AP. Sometimes I couldn't even reconnect, like if I just turned off the adapter, giving me the only option of restarting the system. Sometimes, network manager kept asking me for the WEP key.

**<EVERY TEST I TRIED>**
   After following the suggestions of some users of this glorious forum, I did the following:

1) Change auth/enc from WEP to WPA:
   I did it on both of my AP's (from now on AP1 and AP2, look under <EQUIPMENT>). I set AP1 to WPA and AP2 to WPA2. I notice a difference in AP1, as I could stay connected a whole night without a single problem, but, I had to stay no more than 20 meters away. The speed was even better using WAP on AP1, even in Win7. I didn't see any difference in AP2, things were just the same like when it was WEP (good in Win7, bad in Ubuntu). So, since the results where unacceptable I changed AP2 to WAP too and see if I could stay connected several hours like with AP1, but no success.

*NOTE: I have to mention that I notice a gain of speed on both wireless when I changed them from WEP to WPA. You should give it a try if you still have WEP. Also take in mind that WEP is less secure.

2) Replace Network-Manager with Wicd:
   I didn't see any difference by doing this, but I have to say that Wicd has better interface and also, has better network management. It's even more organized so I really recommend it. As I say, it didn't solve anything for my wireless problem but at least I found a better choice.

* EDIT: Before leading to the final solution described at the end, I was trying to connect to my wired network using Network-Manager (I had to switch back from Wicd to Network-Manager to make some tests) and I had some troubles to make it recognize my network. I connected the cable and nothing happened, like if my Ethernet was turned off, very odd. So I really recommend that you give Wicd a try.

3) Replace the ath9k drivers with the Madwifi-ng drivers:
   No luck at all, the wireless adapter was not even detected. I tried to read the Madwifi documentation to see the compatibility list but they were having some server problems (a lot of 404 errors). I check and recheck my installation, the modules were loaded like they had to, so my bet is that my adapter is not yet supported by Madwifi, period. I even went back to Network-Manager (just to see if miracles exist :P) but no luck at all. I had to revert changes and reload ath9k drivers.

4) Again, replace Network-Manager because of some problems with my wired network, like I wrote in the edit before.

**<FINAL SOLUTION>**
   Reading some other threads I had two more things to do. Try the compat-wireless drivers or go back to Intrepid. But suddenly I saw a post where someone said to just install **linux-backports-modules-karmic** and that would fix the problem. So, I gave it a try, anyway, I had nothing to loose.

   I went to Synaptics and installed linux-backports-modules-karmic, restarted the system and ... let me see where's the difference ... same modules, Wicd is acting normal, no error messages, no difference at all so I connected to my AP2 (The more problematic one) and started to watch some videos on Youtube. The signal seems a little more weak than before but surprisingly it is stable as hell (30 mts away and 41%-48%, it's pretty good considering the signal has to travel through some doors, some walls, go outside, get up some stairs, another door and then my lap). I decided to make a final test, leave it connected while I sleep.

   Well, I left it at 10pm of yesterday. I woke up now, at 5am to go to the bathroom, raise the lid and WHALA!!! it's still connected. You can't imagine how good I feel. Now I'm going to have sweet dreams.

   Sorry if it was so long but I did it so I can help someone else with the same problem. I hope this post helps some souls out there and please, always post your result no matter the problem, no matter the method, so we can all help each other.

Sorry for the long post but I had to,
Sincerely,
X-TBT a.k.a. The Mentor.

---

### Post by moore.bryan on 2009-11-21
XTBT: That's great! Unfortunately, for me, nothing I do can *solve* the problem; everything's only a stop-gap measure. For example if I do the following my network is *minorly *more stable, but still suffers intermittent drops:

[LIST=1]
[*] install *linux-backports-modules-karmic*
[*]install *bind9* and set the line *nameserver 127.0.0.1* in /etc/resolv.conf
[*]change router to WPA-TKIP rather than WPA2-PSK (AES)
[*]statically set ip
[*]uninstall couchdb (according to some of the other conversations I was in it seemed to be causing *some* kind of problem
[*]make all necessary changes to /etc/nsswitch.conf dealing with *mdns4_minimal *and* mdns4*
[/LIST]
  Not quite sure how Karmic's a "release candidate" if these problems still persist. A quick perusal of Launchpad shows *many* similar issues, so it's not "just us."

---

### Post by xtbt on 2009-11-21
> **moore.bryan said:**
> XTBT: That's great! Unfortunately, for me, nothing I do can *solve* the problem; everything's only a stop-gap measure. For example if I do the following my network is *minorly *more stable, but still suffers intermittent drops:

[LIST=1]
[*] install *linux-backports-modules-karmic*
[*]install *bind9* and set the line *nameserver 127.0.0.1* in /etc/resolv.conf
[*]change router to WPA-TKIP rather than WPA2-PSK (AES)
[*]statically set ip
[*]uninstall couchdb (according to some of the other conversations I was in it seemed to be causing *some* kind of problem
[*]make all necessary changes to /etc/nsswitch.conf dealing with *mdns4_minimal *and* mdns4*
[/LIST]
  Not quite sure how Karmic's a "release candidate" if these problems still persist. A quick perusal of Launchpad shows *many* similar issues, so it's not "just us."

moore.bryan: Did you already try the new Madwifi drivers ??? In my case those didn't help maybe because of some kind of incompatibility but you might as well have good luck with them. What's the Adapter you're having trouble with?

---

### Post by moore.bryan on 2009-11-22
> **xtbt said:**
> moore.bryan: Did you already try the new Madwifi drivers ??? In my case those didn't help maybe because of some kind of incompatibility but you might as well have good luck with them. What's the Adapter you're having trouble with?

Yeah, already tried them without success. In Madwifi's defense, though, the Thinkpad I use *never* liked those drivers.

---

### Post by Nalle Berg on 2010-04-09
> **lokutus25 said:**
> My situation is eeePC 1101HA with a fresh install of Karmic. The WiFi Adapter is Atheros AR9285 and my problem is the same as yours...very slow network speed.
I read about an IPV6 problem...is there a useful thread?

Well I also have an EEE 1101 HA. Had the same problem. The problem has not come back after I installed Wicd according to this article: 

[http://ricardocabello.com/blog/post/679](http://ricardocabello.com/blog/post/679)

Nalle Berg
./nalle.

---

