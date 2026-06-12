---
title: "LAN Setup Between Vista and Ubuntu"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by superkop007 on 2009-02-11
hey guys...
i am relatively new to ubuntu and very new here...
i have 2 boxes, one is a desktop with ubuntu and is directly having a wired connection with the ADSL router through an ethernet card...
the other is a laptop with Vista which connects to the internet using a wireless network...

Pardon me as i have never set up a LAN before and i could really use some help...
the thing is that i connected the ethernet card to the wireless router which is then connected to the main ADSL router...
so when i switch on the linux box the wireless router shows 1 PC connected to the network...
then when i try accessing the wireless using my laptop, it grants the access but still only shows 1 comp on the network and neither of the boxes are able to detect each other on the network...
everything else works fine except that there is no network between the 2...

i have a netgear wireless router but didnt install the router configurations to get a secured connection as the CD they gave didnt work on ubuntu, it only works on windows...
so till now everything is just plugged in and the net access is there and it's working but how do i start to create a file sharing network between the 2 comps...

i dont even know the first step, i tried installing the router on my windows box but it said you should only install on a pc with a wired connection so i didnt di it... then i heard about samba and read some stuff about it but i still have doubts on how to do it from the windows end...

i would really appreciate it if you guys could tell me how to start and guide me through it...

thanks a lot

Rey

---

### Post by KaiHeimann on 2009-02-11
Glad to see you here mate.

If you can access the Internet through both devices that means that you have a working network, otherwise we need to troubleshoot that first. The most likely cause for them not being able to talk is that they are not on the same logical network. You will probably find that the laptop is on one network name and the Ubuntu box is on another network name.

If you have any more information then I can probably help further.

---

### Post by superkop007 on 2009-02-11
the Windows box connects to the default unsecured network called NETGEAR with the wireless router...
i dunno how to check which network i am connected to on ubuntu...
the strange thing is that both ping perfectly for the same ip address...

but is there a way to set up a secured wireless on my router without using the proprietary software they gave me?? that thing doesnt work on ubuntu so i cannot setup a secured password protected connection...

---

### Post by KaiHeimann on 2009-02-11
Okay, the network that you want to set up (secure) is available through the web interface of your wireless router. The IP address of your router will be the same as the gateway address of your system that is connected to it. In Linux you can check this by typing
```
ifconfig
```
and then seeing what the gateway address of your connected interface is.

Just type the address into your browser bar and this should take you to your router interface. It is likely to have a password, but should be simple, like 
[LIST]
[*]User: Admin Password:Admin
[*]User: admin password: admin
[/LIST]
etc...

You can usually setup a network directly here, there should be a user guide available through the interface. The network that I am talking about is the network name that you gave the network when you set it up.

Have a look [here]("http://www.howtodothings.com/computers/how-to-setup-a-secure-wireless-network-in-your-home") and it will give you some ideas

---

### Post by superkop007 on 2009-02-11
the router login thing has already been done...
actually i had already installed the ADSL router a couple of months back using the routerlogin and recently i bought a wireless router for the laptop and i noticed that just by plugging it into the ADSL router the wireless network worked so i didnt bother much...

now i bought an ethernet card and tried setting up a file share but the router login is already configured...
should i try to configure it again ?

thanks for taking the time to help me though... really appreciate it...

---

### Post by superprash2003 on 2009-02-11
in your ubuntu machine type ifconfig in the terminal.. and you should see the ip address of ubuntu mostly of the form 192.168.1.x or 192.168.0.x .. 
 in your windows machine type ipconfig in the command prompty and you should see the ip address of windows mostly of the form 192.168.1.x or 192.168.0.x ..
 note down both ips.. try pinging ubuntu machine from windows and vice-versa by typing ping x.x.x.x where x.x.x. are the ips you noted down earlier.
  Once you are successfully able to ping , it means you have a network.. then just use samba to share files and folders..

---

### Post by stussy on 2009-02-13
I have a similar problem.  I followed your advice supersprash2003, and I can ping from Vista and it works fine, but if i ping from Ubuntu to Vista it says:

```
PING 192.168.*.* (192.168.*.*) 56(84) bytes of data
```

and then stops

---

### Post by stussy on 2009-02-13
I had to add my ubuntu's IP as a trusted source on my Virus Protection's Firewall on the Vista machine

---

### Post by superkop007 on 2009-02-13
hey stussy...
the same things happening to me as well..

i am able to ping the ubuntu machine from vista but when i try the other way around it says destination net unreachable..

any suggestions here???

---

### Post by stussy on 2009-02-13
hi superkop, do you have any virus protection like mcAfee installed on the vista machine?  If you do, you need to add your Ubuntu machine's ip as a trusted source.

---

### Post by FishRCynic on 2009-02-14
[http://ubuntuforums.org/archive/index.php/t-388337.html](http://ubuntuforums.org/archive/index.php/t-388337.html)


i have been posting these ideas to fix these issues but the above is
still very relevant and saves me typing (besides i have obviously reinvented the wheel - again) 

the only thing i would add is that before i save to a share i always
browse it in nautilus first

---

### Post by superprash2003 on 2009-02-14
did you ping 192.168.*.* or some no like 192.168.1.10 ??

---

