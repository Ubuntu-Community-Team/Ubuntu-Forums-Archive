---
title: "can I configure NetworkManager?"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by ssalman on 2006-06-07
Is there a way to configure NetworkManager to connect to WPA wireless networks without asking for a password? not the wpa passphrase, I'm asking about the NM password.
   
  Is there any way to configure NM, for example to change the ESSID preference?

---

### Post by zahidism on 2006-06-07
i've wondered this too

---

### Post by ssalman on 2006-06-08
Found the following statement on the NM web site:

"When moving into areas you've been before, NetworkManager automatically connects to the last network the user chose to connect to. Likewise, when back at the desk, NetworkManager will switch to the faster, more reliable wired network connection."

but I'm still wondring if I can modify it's configuration, and if I can bypass the anoying password request??

---

### Post by ilhyfe on 2006-06-08
I wonder which "Network Manager" you are talking about. I'm new to Ubuntu and the "Network Manager" which comes with gnome only supports WEP (in my case).

Regards

---

### Post by TearGas on 2006-06-08
> 1. install wpa_supplicant
2. install Network-manager-gnome
3. Comment out everything but "lo" entries in /etc/networks/interfaces
4. Create a file called /etc/default/wpasupplicant, add entry "ENABLED=0"
5. Reboot
6. Select your network in the NM icon
7. Follow the prompts for password, type, etc.
8. Choose password for keyring (you'll be prompted).
9. Away you go!
by geocritter

[http://www.ubuntuforums.org/showthread.php?t=179643](http://www.ubuntuforums.org/showthread.php?t=179643)

---

### Post by ssalman on 2006-06-08
Wait!!... I did nothing of what you are talking about but still had my wireless card (artheos chipset) working with WPA out of the box after installing dapper and NM, I did a fresh install, not an upgrade.


I guess my question is how do I skip the keyring password, and how do I configure NM?

---

### Post by kiwiboyus on 2006-06-08
I have been trying almost every suggestion posted about setting up WPA but I still only see the option for WEP in Network Manager. This maybe a stupid question but if all goes correctly will I actually see WPA listed in NM as well as WEP? Is there any way to tell if you are even half way there without actually trying to connect to a WPA access point? :confused:

---

### Post by ComplexNumber on 2006-06-08
[quote=ssalman]Wait!!... I did nothing of what you are talking about but still had my wireless card (artheos chipset) working with WPA out of the box after installing dapper and NM, I did a fresh install, not an upgrade.


I guess my question is how do I skip the keyring password, and how do I configure NM?[/quote]
the only ones that i did in that list was 2 and 8....and mine's working.

---

### Post by calcifer on 2006-06-09
[QUOTE=kiwiboyus]I have been trying almost every suggestion posted about setting up WPA but I still only see the option for WEP in Network Manager. This maybe a stupid question but if all goes correctly will I actually see WPA listed in NM as well as WEP? Is there any way to tell if you are even half way there without actually trying to connect to a WPA access point? :confused:[/QUOTE]

There are two different entities here: Network Settings and Network Manager. Network Settings is the control-panel like interface for setting up your network hardware....except that afaik it doesn't support WPA as an option yet. Network Manager is a separate program (not installed by default, you have to apt-get it) designed primarily to manage wireless connectivity. Manager -does- support WPA.

---

### Post by ssalman on 2006-06-09
I think my thread has been officially hijacked!!  :)
   
  I don&#8217;t mean to be rude, but I&#8217;m still looking for an answer for how do I skip the keyring password, and how do I configure NM?

---

### Post by ComplexNumber on 2006-06-09
[quote=ssalman]I think my thread has been officially hijacked!!  :)
   
  I don’t mean to be rude, but I’m still looking for an answer for how do I skip the keyring password, and how do I configure NM?[/quote]
i'm not too sure if there is a way to connect without a password. i never encountered it while i was learnign how to set up my network anyway. i think its meant to be like that.

---

### Post by ssalman on 2006-06-09
[quote=ComplexNumber]i think its meant to be like that.[/quote] 
If that is true, that will mark the first time I run into unconfigurable software in Linux...[FONT=&quot]:shock:[/FONT]

---

### Post by HunterPro on 2006-06-09
[QUOTE=ssalman]If that is true, that will mark the first time I run into unconfigurable software in Linux...[FONT=&quot]:shock:[/FONT][/QUOTE]
I had the exact same thought. Its weird that you have to install a network manager with some sort of a hack (you can't call clearing out your INTERFACES file clean ;)) and after that you'll just have to hope and pray that it works.

It works here now, but my eduroam/university of Twente WPA account doesnt work. I tried both WPA enterprise and WPA2 enterprise, filled in my user details, fed the thing my pa certificate, and it couldnt connect. With a manual wpa_supplicant -iath0 -Dmadwifi -B -c/etc/wpa_supplicant.conf [enter] (that conf is one that I made earlier and has been thouroughly tested, and also doesnt feature anything fancy) it connects within a second.

Its a nice tool probably, but completely useless for me. And this way, I guess, for a lot of non-noob users too. Give us some .confs! :-)

---

### Post by JazzCrazed on 2006-06-10
I really could use help with this, as well. It seems as if every time I first boot into Ubuntu, NM bugs me for the keyring password several times in a row when trying to connect to my AP (which uses WPA2, though these symptoms also affected me with a WEP AP before). It doesn't even let me finish typing in the keyring password in the first prompt, before another prompt pops up. It's very annoying!

---

### Post by siriusnova on 2006-06-10
[QUOTE=JazzCrazed]I really could use help with this, as well. It seems as if every time I first boot into Ubuntu, NM bugs me for the keyring password several times in a row when trying to reonnect to my AP (which uses WPA2, though these symptoms also affected me with a WEP AP before). It doesn't even let me finish typing in the keyring password in the first prompt, before another prompt pops up. It's very annoying![/QUOTE]


This is what you are looking for:
[http://ubuntuforums.org/showthread.php?t=187874&highlight=PAM+networkmanager](http://ubuntuforums.org/showthread.php?t=187874&highlight=PAM+networkmanager)


i did that and it works flawlessly for me...
make sure your keyring password and login password is the same

---

### Post by JazzCrazed on 2006-06-10
Siriusnova, that was perfect! Thanks... I feel silly I didn't find that already. 	:oops:

---

### Post by JazzCrazed on 2006-06-12
OK, I lied... It worked the first few times, but just now it asked me twice in a row for the keyring password.

Going to reboot a few times to see if it still happens.

---

