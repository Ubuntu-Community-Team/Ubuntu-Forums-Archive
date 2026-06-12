---
title: "how do i turn my laptop into wifi hotpot?"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by hgjybrandon on 2011-05-14
hi, i am proudly running ubuntu 10.10 on my laptop, and i have a wired Motorola modem connected to my laptop, for the next couple of months, more than one laptop will be in the house, is there some way to turn my laptop into a wifi hotspot on ubuntu 10.10
- any help is needed, and valued-

---

### Post by gsparky2004 on 2011-05-14
The short answer is, "Yes, you can do it."

The longer answer is, "It will require some work."

How put off are you by having to load software and change network settings?

I'll walk you through it, but if any of this scares you, you might just want to invest in a small wireless router.

---

### Post by hgjybrandon on 2011-05-14
> **gsparky2004 said:**
> The short answer is, "Yes, you can do it."

The longer answer is, "It will require some work."

How put off are you by having to load software and change network settings?

I'll walk you through it, but if any of this scares you, you might just want to invest in a small wireless router.
  im okay with it, i got enough gb, i would love your help!

---

### Post by gsparky2004 on 2011-05-14
Also,
- what kind of devices do you want to have use your "access point"?  Are they laptops running Mac or Windows or Linux?  Wifi-capable smartphones?
- What level of networking skills do you have?  Do you understand DHCP, DNS, NAT, and IP forwarding?
- If your laptop is using an Atheros-based wireless card, you might be able to set up as a full-fledged access point; otherwise, some things you will have to set manually on the mobile device.

---

### Post by hgjybrandon on 2011-05-14
> **gsparky2004 said:**
> Also,
- what kind of devices do you want to have use your "access point"?  Are they laptops running Mac or Windows or Linux?  Wifi-capable smartphones?
- What level of networking skills do you have?  Do you understand DHCP, DNS, NAT, and IP forwarding?
- If your laptop is using an Atheros-based wireless card, you might be able to set up as a full-fledged access point; otherwise, some things you will have to set manually on the mobile device.
- only two laptops running ubuntu 10.10 , one wifi capable smart phone will use the hotspot
- i do not understand DHCP, DNS,or nat :(

---

### Post by gsparky2004 on 2011-05-14
> im okay with it, i got enough gb, i would love your help!
Understand that its not the "gb" (which I'm assuming means "gigabytes" as in you have enough storage space on your hard drive), it's the amount of work that you'll need to do not only for your laptop that will become the Wifi connection, but on the mobile devices, too.
That said, let's start (relatively) easy.  We'll create a connection between your laptop and another device over the wireless interface.  
First, we need to find out what your wired connection settings are.  To get this information, right-click on the network manager icon and select "Connection information".  (NOTE:  That's the connection that appears in the upper, righthand corner of your screen and is typically next to the icon for your sound and for your Evolution e-mail.) This will tell you your IP address and, more importantly, the "Route" and "Primary DNS".  Note those two things (route and primary DNS).  
We're going to start by creating an ad-hoc network connection on your laptop.  Right-click on the network manager icon and select "Edit connections".  In the window that opens, select the "Wireless" tab and click on the "Add" button.  Here are the values to enter in the various windows:
- Connection Name:  Whatever you want to call it, such as "My Hotspot".
- SSID: This will be the "name" of your hotspot that others might see to connect to it.
- Mode:  Select "Adhoc"
- Band: I suggest selecting "B/G".
- Channel: You can either leave this as is, or choose a specific number.  If you're in the US, it will have to be a number between 1 - 11.  I've found that 11 tends to work best because most people choose either the default (which is 6 normally) or 1.
- BSSID: Leave blank.
- Device MAC Address: Leave blank.
- Cloned MAC Address: Leave blank.
- MTU: Leave as "automatic".

Don't hit "Apply" yet.  Select the "Wireless Security" tab and make sure it says, "None".

Now select the "IPV4 Settings" tab.
- Method: Choose "Manual".
- Next to "Addresses" click "Add".
- Under the "Address" column, enter "192.168.100.1", with a netmask of "255.255.255.0".  Under "Gateway", enter the IP address you got from "Route" in your wired connection.  For example, here at my house, my IP addresses are 192.168.1.x.  The router (a Fios-provided router) is at 192.168.1.1.  That's the IP address I would put in under "Gateway".  For you, I'm assuming you have a Motorola cable modem.  Put in the IP address of that (which should be the same as what you got from "Route" for your wired connection.)  Under DNS servers, put the IP address you got for "Primary DNS" of your wired connection.  For the secondary DNS, I always put "8.8.4.4", which is a Google public DNS server.
- Leave the box checked that says, "Require IPv4 for this connection to complete".

Now click "Apply".

Now,*LEFT*-click on your network manager icon and select "Connect to Hidden Wireless Network".  Next to where it says "Connection", click on the drop-down menu and you should see the name of the connection you just created.  Select it and then click on "Connect".

At this point, your laptop can be become part of an ad hoc network.  You should see the network manager begin flickering, then it should announce "My HotSpot connection established" (or whatever you named your wireless connection).

Leave it up for a minute or two, then see if any of your other wireless devices can "see" it when looking for available wireless connections.

Once you get to this point, let me know.

---

### Post by hgjybrandon on 2011-05-14
> **gsparky2004 said:**
> Understand that its not the "gb" (which I'm assuming means "gigabytes" as in you have enough storage space on your hard drive), it's the amount of work that you'll need to do not only for your laptop that will become the Wifi connection, but on the mobile devices, too.
That said, let's start (relatively) easy.  We'll create a connection between your laptop and another device over the wireless interface.  
First, we need to find out what your wired connection settings are.  To get this information, right-click on the network manager icon and select "Connection information".  (NOTE:  That's the connection that appears in the upper, righthand corner of your screen and is typically next to the icon for your sound and for your Evolution e-mail.) This will tell you your IP address and, more importantly, the "Route" and "Primary DNS".  Note those two things (route and primary DNS).  
We're going to start by creating an ad-hoc network connection on your laptop.  Right-click on the network manager icon and select "Edit connections".  In the window that opens, select the "Wireless" tab and click on the "Add" button.  Here are the values to enter in the various windows:
- Connection Name:  Whatever you want to call it, such as "My Hotspot".
- SSID: This will be the "name" of your hotspot that others might see to connect to it.
- Mode:  Select "Adhoc"
- Band: I suggest selecting "B/G".
- Channel: You can either leave this as is, or choose a specific number.  If you're in the US, it will have to be a number between 1 - 11.  I've found that 11 tends to work best because most people choose either the default (which is 6 normally) or 1.
- BSSID: Leave blank.
- Device MAC Address: Leave blank.
- Cloned MAC Address: Leave blank.
- MTU: Leave as "automatic".

Don't hit "Apply" yet.  Select the "Wireless Security" tab and make sure it says, "None".

Now select the "IPV4 Settings" tab.
- Method: Choose "Manual".
- Next to "Addresses" click "Add".
- Under the "Address" column, enter "192.168.100.1", with a netmask of "255.255.255.0".  Under "Gateway", enter the IP address you got from "Route" in your wired connection.  For example, here at my house, my IP addresses are 192.168.1.x.  The router (a Fios-provided router) is at 192.168.1.1.  That's the IP address I would put in under "Gateway".  For you, I'm assuming you have a Motorola cable modem.  Put in the IP address of that (which should be the same as what you got from "Route" for your wired connection.)  Under DNS servers, put the IP address you got for "Primary DNS" of your wired connection.  For the secondary DNS, I always put "8.8.4.4", which is a Google public DNS server.
- Leave the box checked that says, "Require IPv4 for this connection to complete".

Now click "Apply".

Now,*LEFT*-click on your network manager icon and select "Connect to Hidden Wireless Network".  Next to where it says "Connection", click on the drop-down menu and you should see the name of the connection you just created.  Select it and then click on "Connect".

At this point, your laptop can be become part of an ad hoc network.  You should see the network manager begin flickering, then it should announce "My HotSpot connection established" (or whatever you named your wireless connection).

Leave it up for a minute or two, then see if any of your other wireless devices can "see" it when looking for available wireless connections.

Once you get to this point, let me know.



----ive gotten to the last part, it wont let me click apply, it still has two more boxes left in the Ipv4 setting & thats the search domain, and the DHCP client id.. what do i enter for that?

---

### Post by hgjybrandon on 2011-05-14
never mind, i figured it out, i have completed the steps ( im ready for the next steps)

---

### Post by gsparky2004 on 2011-05-15
Just to confirm, after you ran through those steps, did you use your other laptop or mobile device and see your "hotspot" listed as an available network?

If so, I want you to try to connect to it with your other, Ubuntu-equipped laptop.  To understand what comes next, I want you to understand what happens when you connect your Ubuntu-equipped system to a normal access point.  For this discussion, I'm going to assume the access point is just a normal, home-based access point that's using WPA (Wifi Protected Alliance) encryption.  I'm also going to assume that it also has a DHCP server(Dynamic Host Configuration Protocol, or that thing that gives you your IP address, gateway and DNS addresses when you connect.)

The first three steps for forming a connection are "authentication", association, and encryption.  During this time, if you watch the Ubuntu network manager icon (the one that looks like a series of lines radiating from bottom to top), it will have a bright line bouncing up and down.  If it continues to bounce up and down, that means that something has gone wrong with either one of these three steps.  Most likely, the problem is with the encryption and you either have the wrong encryption type set (WPA when it wants WPA2, or WEP when it wants WPA, etc) or the wrong password.  It's rare for there to be a problem with the "authentication" (which I'm putting in quotes because its not real authentication, it's just the mobile device essentially saying, "Hello, I'm a device wanting wireless connectivity" to the access point.) or the association.  The problem is typically with the encryption.  That's why if you have a problem with one of these steps, the end result is that Ubuntu puts a screen up prompting you for the password.  Ubuntu assumes that you have the password wrong because that's the most likely problem.

If Ubuntu gets through those first three steps correctly, the network manager icon will start going just from the bottom to the top, then keep cycling from bottom to the top.  At this point, it's now connected to the *access point*, but it's *not connected to the network*.  Normally, your mobile device or laptop will use DHCP to ask for an IP address, a gateway address (that's the IP address to send all packets not destined for your local network, meaning typically packets destined for the internet), and a DNS server address.  DNS (Domain Name System) is how the internet converts web names (Ex: "www.google.com") into IP addresses (Ex: 76.118.19.101).  Once that icon is just radiating from the bottom to the top (not up and down, just from down to up), it's trying to find a DHCP server.  This is a service your normal wireless router provides.  

Once your system has found a DHCP server, it is assigned an IP address and informed what the gateway address and DNS server address are.  At this point, it is connected.  And on your Ubuntu system, the network manager icon will go to all of the lines becoming solid and you typically get the "Connected" message flashing on your screen.

That all said, when you try to connect your other Ubuntu laptop to your new "hotspot", does it connect, or does it stop either when the lines are bouncing up and down (problem with authentication, association or encryption) or when they are just going from bottom to top (problem with DHCP)?

---

### Post by livin4th on 2011-12-11
Hi,
           I followed  the post to the letter and I was able to create and connect to the ad-hoc network on the laptop. The problem now is that I cannot see the network on any other device (smartphone)..It keeps scanning but without any listed connections. What should I do now?

Thanks in advance.

Livin

---

### Post by tumutanzi.com on 2012-05-19
I have not tried on Ubuntu 10.10. But I tried on Ubuntu 10.04 and Ubuntu 12.04, successfully.

For 12.04, the detailed tutorial: [http://tumutanzi.com/archives/8195](http://tumutanzi.com/archives/8195)
For 10.04, the detailed tutorial: [http://tumutanzi.com/archives/3293](http://tumutanzi.com/archives/3293)

Good luck, hope it can helps you.

---

### Post by foxy123 on 2012-08-25
> **tumutanzi.com said:**
> I have not tried on Ubuntu 10.10. But I tried on Ubuntu 10.04 and Ubuntu 12.04, successfully.

For 12.04, the detailed tutorial: [http://tumutanzi.com/archives/8195](http://tumutanzi.com/archives/8195)
For 10.04, the detailed tutorial: [http://tumutanzi.com/archives/3293](http://tumutanzi.com/archives/3293)

Good luck, hope it can helps you.

Has gone through the tutorial for 12.04 but cannot see the hotspot on my Galaxy S2. I've got Asus U36jc laptop.

---

### Post by foxy123 on 2012-08-25
Booted to Win7 to check if my laptop supports wifi hotspot. Did not manage to makeit work with built-in Win7 tools but downloaded Connectify and it worked. So I wonder what is the problem with Ubuntu.

---

### Post by foxy123 on 2012-09-05
Just for those for whom like for me this tutot=rial does not work, you can try [this one]("http://thenewbieblog.wordpress.com/2012/05/01/wifi-hotspot-setup-on-ubuntu/"). It works fine but requires editing system files and some command line.

---

### Post by princesidney. on 2013-05-17
but can Connectify work on Linux 13.04 using wine?

---

