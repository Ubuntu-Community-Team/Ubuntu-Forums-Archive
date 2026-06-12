---
title: "Cannot connect to home wireless router but can connect to public wireless router"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by dualslash on 2010-08-31
I am having some trouble getting my netbook and my desktop connecting to the internet on my home wireless router. When I am at school I can connect to the school's router with no problems. I am guessing that the two system have the same problem. Both run lucid lynx the netbook has 32 bit edition and the desktop has 64 bit. I know my wireless router works because I am able to connect with a windows laptop. Also, as a note, both of the ubuntu systems recognize the router but are unable to connect. Thanks in advance.

---

### Post by dualslash on 2010-08-31
I also forgot to mention that I have connected a few times with the my desktop system at my home wireless network, but not with my netbook.

---

### Post by Tracy177 on 2010-08-31
> **dualslash said:**
> I am having some trouble getting my netbook and my desktop connecting to the internet on my home wireless router. When I am at school I can connect to the school's router with no problems. I am guessing that the two system have the same problem. Both run lucid lynx the netbook has 32 bit edition and the desktop has 64 bit. I know my wireless router works because I am able to connect with a windows laptop. Also, as a note, both of the ubuntu systems recognize the router but are unable to connect. Thanks in advance.

WHAT wifi card do you have ?

did you try to use wicd instead network manager ?

and what encryption did you try to connect without encryption?

---

### Post by dualslash on 2010-08-31
my netbook has a Atheros AR5001 and my desktop has a RaLink RT2500(its a old linksys card). No I have not used wicd, I will try installing it and see what the result is. I have tried turning the wireless security off and tried WEP and WPA2. Normally I have it set to WPA2.

---

### Post by varunendra on 2010-09-01
Does your router have DHCP enabled, or do you use static IP for your laptop & computer?

What is the IP of your router?

If your windows laptop is still around, connect it to the wifi, open command prompt (All Programs>Accessories>Command Prompt) and enter this command:
```
ipconfig /all > "%userprofile%"\desktop\ipconfig.txt
```This will generate a file named ipconfig.txt on your desktop. Open it & post its contents here.

Now start ubuntu on your netbook, switch on its wifi (if there's a switch or hotkey for it), open terminal (Applications>Accessories>Terminal) and enter these commands:
```
sudo lshw -C network
ifconfig -a
iwconfig
route -n
sudo dhclient
```Post back the outputs of each of the above commands.

To post the outputs, just copy them, paste here in your post, then highlight **only** the pasted output, and click on the **# **icon at the top panel of the editing window. Do this separately for each output.

---

### Post by dualslash on 2010-09-07
I downloaded wicd and made a change to my router configurations (changed a mac address option, don't know if it actually did anything though). After that I was able to connect to my router with no problems. Thanks for your help.

---

