---
title: "Wireless stops working unless I broadcast SSID"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by kuriharu on 2006-06-07
Ok, so here's a weird one. I finally got wireless to work, but it only works if I broadcast the SSID from my WAP. If I connect then turn off SSID broadcasting, it works fine, too. But if I turn off SSID broadcast and reboot, I can't connect at all no matter how many times I try (okay, I give up after 6-7 tries). 

Anybody have any clues? Since I have MAC address filtering on encryption enabled I'm not too worried, but it would be nice to leave it off.

---

### Post by briangs on 2006-06-07
MAC address filtering is an essentially useless method to prevent attacks, as is turning off your SSID broadcast. If SSID broadcasting works, you might as well just leave it on.

---

### Post by kuriharu on 2006-06-07
Neither method is worthless, especially MAC filtering. You're assuming all attacks come from experienced crackers. You don't leave your car unlocked just because someone could throw a rock through the windshield.

Having the SSID broadcast makes my Windows partition not connect automatically and the same thing happens to Ubuntu sometimes. I guess I was foolish for thinking I could get Ubuntu to function as easily as Windows. *Sigh!*

---

### Post by phace on 2006-06-08
It works normally. I have no problem when my SSID is not broadcasting... post here the output of dmesg

---

### Post by tramahound on 2006-09-01
I'm in the same boat. dmesg basically says "link is not ready" for my wireless connection. 
I can't get this set up to work under xp either and was hoping it would at least work for ubuntu since then I could at least boot into that while at home. I'm wondering if the password part of the configuration is the problem. I don't have a passkey as I just have ssid off and mac filtering on. all my other computers/appliances connect to this network fine...
Thanks

---

### Post by acegolfer on 2006-10-24
I'm in the same shoe.

I have wireless-G WPA home network (forgot the router model) set up. My Ubuntu laptop can connect wirelessly using network-manager as long as the SSID is broadcast. Once hidden, can't connect it after reboot.

---

### Post by BungaMan on 2006-12-12
Seems like the thread silenced without a solution... I have the same problem that wireless works with SSID broadcast.  Without broadcasting it doesn't connect.  Anyone who can point to a solution for this?

my portable has an ipw2200 (intel centrino)
and my wap is a Vigor 2800VG

---

### Post by emdeem on 2006-12-12
Anecdotally, it seems that this problem is most often reported when trying to use no SSID broadcast along with WPA.  That's certainly true for me, and I have found no solution other than to leave SSID broadcast on.

FWIW, I have had the same experience using wpa_supplicant, NetworkManager, etc in Fedora.

---

### Post by FrodoB on 2006-12-12
If WPA-PSK or WPA-something is the problem then look into ap_scan:

ap_scan=1  # Broadcast SSID

ap_scan=2 # Hidden SSID

Hope that helps some of you anyway.

---

### Post by alexjr on 2006-12-12
Thats strange I use Wireless assistant in Ubuntu and I can connect to networks that don't droadcast their SSID's. For example right now I can view two networks. One is WEP secured and one does not broadcasts its SSID for security. But wireless assistant picks up its MAC. I can connect to the one that is not broadcasting It's SSID. Infact I'm connected to it now. Therfore simply not broadcasting the SSID is not enough. Unfortunatly who ever secured this network thinks so. :(
If you are not using wireless assistan to connect wirelessly I recommend you give it a try.

---

### Post by shearn89 on 2006-12-29
I tried wireless assistant, and although I could see my network, I couldn't connect to it - I would input all the settings, and then it would try to connect and just fail. Although, I have tried loads of different methods to connect to my AP, and none of them have worked, so it could just be my hardware and set up - it was configured by one of the technicians at my dad's office, so its uber secure...

---

### Post by SugarDaddy on 2006-12-29
FrodoB is most likely correct. If you are using WPA or WPA2 encryption which requires wpa_supplicant to be installed, then one of the flags that needs to be set for hidden SSIDs is **ap_scan=2**. This can be done in the /etc/network/interfaces file: check the sticky HowTo thread by Weiman01 at the top of this forum on how to do this (link below). Another method for setting **ap_scan=2** is to configure the /etc/wpa_supplicant.conf file itself which is useful for configuring multiple APs (second link). The last link is especially useful for installing wpa_supplicant or at least making sure it is installed, debugging, etc.

[URL="http://ubuntuforums.org/showthread.php?t=318539"]http://ubuntuforums.org/showthread.php?t=318539
[/URL][http://ubuntuforums.org/showthread.php?t=324545](http://ubuntuforums.org/showthread.php?t=324545)
[URL="http://www.ubuntuforums.org/showthread.php?t=263136"]http://ubuntuforums.org/showthread.php?t=263136
[/URL]
Hope this helps!

---

### Post by tturrisi on 2006-12-29
Disabling SSID Broadcast is a very very very low level layer of security, in fact it is all but useless to disable it.  The ssid is sent in every packet header that goes out of the AP, thus if a network sniffer is used the ssid can be seen.  It can also be detected by NetStumbler on Windows or Kismet in linux.

---

### Post by SugarDaddy on 2006-12-29
It's posts like the above that reinforce the negative, rude, and snobbish images that linux users have, and why it continues to struggle to effectively compete against M$. Little boy to father: Can I go outside and play? Father to little boy: Sure, but don't use the door, that's way too simple. Climb up the chimney and jump from the roof to the neighbor's tree.

But, let's forget the fact that the question in the thread was how can I get my WiFi to work with my hidden SSID versus commentary on the effectiveness of hidden SSIDs, and examine the logic: my hidden SSID can easily be sniffed so I guess I have no choice but to broadcast it, encryptions can be cracked so I guess I have to leave my router unlocked. As one user eloquently commented: just because slimjims exist doesn't mean I leave my car unlocked and if I got a garage to park it in out of sight from the public, why on earth would I leave it parked around the corner instead? Oh, I forgot, because someone could break into the garage and steal it anyway.

But more to the point, if you don't know the answer or have a suggestion you have no business commenting: it just degrades the community. This is the kind of stuff moderators need to be watching out for.

---

### Post by tturrisi on 2006-12-29
I don't disagree w/ what you say.  Perhaps I should have given my response more thought.   You are correct in that advances to linux grow from solutions discovered as linux evolves.

I would also like to point out that 'disable ssid broadcast' was not really ever meant to be a security layer, but more so a 'privacy' tool.  Disabling it does have use for APs in dense public areas such as business districts and possibly appartmet-townhouse complexes.  But for residential suburban areas disable-ssid has little value.  What really secures a wlan is the encryption used, along w/ strong keys & pass phrases.

Disable-ssid also means that one must manually config his wlan access, which is somewhat counter to the concepts of 'plug + play' and 'user friendly'.  And manual config of wlan access even in Windows is something the majority of users have no idea how to do. 

Also, I had decided to post my comments because it had appeared that FrodoB had already given the solution, and what followed after that was discussion about other related things.  I apologize.

---

### Post by SugarDaddy on 2006-12-30
Well worded response :) I happen to live in a university high rise and can see 15 personal APs from my apartment. So the privacy feature of hidden SSID is definitely valued.

However, the hidden SSID creates some snags, and while FrodoB is correct in pointing to the ap_scan flag, those who don't even know where to look for the ap_scan flag often benefit from a step by step guide.

---

### Post by tturrisi on 2006-12-30
Yea, in a university setting disable ssid has value.
What each linux desktop environment needs is a versatile front end to wireless-tools along w/ wpa-supplicant.  One could even make some decent money if one developed such an application.

---

### Post by shearn89 on 2007-01-10
I tries everything i could to get my wireless to work - changed every setting possible in the wpa_supplicant config file, tried loads of different GUI tools (network-manager, wireless assistant, etc.), however, no cigar: i think its probably a hardware problem, as it did occaisonally connect, but on connecting the whole system freezes and has to be reset....

---

### Post by BungaMan on 2007-01-11
suggardaddy, thanks for pointing out the ap_scan.  I'll give it a try this evening.

the reason I want to hide the SSID is to avoid accidental connection to my network.  it does add to security in the sense that the SSID is not broadcasted so if you don't use your network then nobody in the neighborhood will be able to detect your network.  At least not a normal user.  on top of that I have mac filtering, strict static IP binding (unknown mac's don't get an address) and WPA enabled so no worries.

---

### Post by PreachersPoker on 2007-02-26
Same issue.  WPA, hidden SSID.

The canned answer of hack up this file or that file does not fit in line with "It Should 'Just Work'(tm)"

For now, I am broadcasting my SSID but this issue needs to be addressed.

---

### Post by jonlatane on 2007-03-07
I can confirm this issue for two networks, and with WEP rather than WPA.  My own, at home, doesn't work with SSID broadcasting turned off.  I can turn it on and it works fine.  Additionally, my university's wireless network doesn't work for me.  It uses the exact same security settings as my home router (WEP 64-bit, no SSID broadcast) and I get the same effect with network-manager (network appears in list when trying to connect, but looks like it has no signal strength).

---

### Post by jonlatane on 2007-03-19
The issue with non-broadcast SSIDs seems to be fixed in the CVS version of NetworkManager.  A friendly fellow has made packages available for Dapper and Edgy available here:

[http://www.ubuntuforums.org/showthread.php?t=235655](http://www.ubuntuforums.org/showthread.php?t=235655)

Since updating to these versions, I have had no more problems.

---

