---
title: "Wifi connection"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by gemone on 2009-04-19
Hello,

I just installed ubuntu today. I have been trying to connect my laptop to my wifi connection but I have been unsuccessful. I tried the function key and that did not work. It's not even seeing my router at all. So I verified my connection by going back into windows and my wifi connection was running fine. Does anyone have any suggestions?

Thanks

---

### Post by gemone on 2009-04-19
Does anyone know what the problem may be?

---

### Post by RedSingularity on 2009-04-19
Type "lspci" in the terminal and post the output.

---

### Post by gemone on 2009-04-19
It pulls up the following info for net and ethernet controller:

net controller: atheros comm. inc. AR928X wireless network adapter pci ex

ethernet realtek semiconductor rtl8111/8168b pci ex gigabit ethernet controller

---

### Post by RedSingularity on 2009-04-19
You probably did this but did you check System>Admin>Hardware Drivers?  You may be able to activate it in there.

---

### Post by gemone on 2009-04-20
Yes I tried that. It is not picking up the wifi adapter. Is there any other options?

---

### Post by gemone on 2009-04-20
I am now picking up a wifi signals (my sig and neighbors). But I am unable to connect with my wep key. It ask for my wep key and then I type it in. It starts loading and ask for it again. I know I am inputting the correct wep key. Can anyone help?

---

### Post by RedSingularity on 2009-04-20
Make sure you are setting the correct type of key for your network.  There are 2 types of wep.

---

### Post by pastalavista on 2009-04-20
Can you connect to the internet by wire? If you can hook into the router by ethernet, you might be able to update to better drivers. Have you done any updates at all?

---

### Post by gemone on 2009-04-20
I am typing the correct key. I verified it several times.
I will try the wired route and see what happens. 
Thanks

---

### Post by gemone on 2009-04-21
Back to square one. Once again I do not have a wifi connection. This is real frustrating.

---

### Post by gemone on 2009-04-21
Back to square one. Once again I do not have a wifi connection. This is real frustrating.I am unable to connect wired bcuz I have fios connection.

---

### Post by RedSingularity on 2009-04-21
Can you turn your WEP off for a minute to see if you can connect wirelessly at all?

---

### Post by gemone on 2009-04-21
I tried that it is not working.

---

### Post by JoshJayK on 2009-04-21
Yeah I'm having the same problem. I looked at the Help thing on Ubuntu, and it said make sure the "Detect Wireless Settings" was checked. So I right clicked the little computer icon on the bar, and I didn't even see a "Detect Wireless Settings" option. Help?

---

### Post by pastalavista on 2009-04-22
Try this
```
sudo apt-get install madwifi-tools
``` and reboot

oh wait.. sorry. you can't connect at all? I don't understand why you can't connect with ethernet. The fios modem doesn't have an ethernet jack? very odd...

---

