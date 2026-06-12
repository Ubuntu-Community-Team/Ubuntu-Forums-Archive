---
title: "cannot enable networking in my ubuntu 10.10."
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by maizuddin35 on 2011-04-07
Hello guys , I need your help with this one. 

I cannot enable my netwoking so that it can detect the wireless and stuffs back . 
Before this happen , remove indicator-network cause im using this indicator network with the default gnome panel. When I enable back my gnome-panel as the default panel. I remove the indicator-network. When I add up back the indicator applet for the gnome panel. The networking indicator is not longer functioning. 

Please see this image 


[IMG]http://i.imgur.com/kPSAq.png%22%20alt=%22%22%20title=%22Hosted%20by%20imgur.com%22%20/%3E[/IMG]

if you guys got anything, please do tell me.
thank you in advance.

---

### Post by grahammechanical on 2011-04-07
In that menu there should be a line that reads, Enable wireless. That is if you have a wireless adapter in your machine. 

Is it a laptop? Do you need to switch on the wireless adapter by a keyboard combination? Are you using another operating system? Did you switch wireless off when using that operating system. If so, then you need to use that other operating system to switch the wireless adapter back on. Is the wireless adapter switched off in the BIOS. Can you use a cable to connect to the modem/router? what happens if you do that?

These are just some questions that might help you. some of them might not apply to you. But we do not know.

Regards.

---

### Post by maizuddin35 on 2011-04-07
thanks for the reply. Im sorry for the lack of information . 
im using ubuntu 10.10
im using a computer desktop.
i use a usb wifi adapter 
I already plug in my usb adapter .
but it seems nothing happen.

Thats the problem , before this happen, the "Enable networking" is working just fine. Now its doesnt. Right now, I can't access the internet with my ubuntu, and im using windows for the time being.

---

### Post by maizuddin35 on 2011-04-07
I had done something with this one. 

I try to install indicator-network back via link i get from synaptic package manager by
going to the synaptic, then, search for "indicator-network"
I click as it will be highlighted 
then, File >> Generate package download script
I save it in txt, or plaing text format, because the download deb link is inside there.

I get back to my windows for internet connection.
copy and paste the link to the browser and download.
it fast cause the size so small.

back to my ubuntu 
open my terminal >> [B]sudo dpkg -i (the downloaded file) 
[/B]now the problem is fix.
just a few things I wanted to know now...will be posting back about this.

---

