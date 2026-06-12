---
title: "Help connecting to Ethernet AND router needed."
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by shizumasa14 on 2009-04-12
I read somewhere online to go to Preferences>Administration>Network.  There is nothing that says network....  how do I connect?  Unfortunately I don't know what kind of router it is because it is my dad's and he won't let me near it.  Or tell me about it.  I just know that it worked in Windows.

1. How were you trying to get online? Ethernet wired, and wireless router.

2. What hardware are you using?  I am using an Acer Aspire 4720z.  The modem that I bought for myself a while ago is an ARRIS.

3. Who is your Internet Service Provider?  Comcast Cable in the United States.

4. Which version of Ubuntu are you using?  Ubuntu 8.10 Intrepid Ibex.

5. Can you get online with any other method?  No.  I have tried using an ARRIS cable modem, but it doesn't work either.

6. How are you getting online to post on this forum?  My mothers Compaq Presario SR1650NX desktop computer running Windows XP.

7. For wifi - what encryption are you using? Have you tried an open network? What wifi channel do you use?  I have no idea.  What does this mean?

8. Do you dual-boot with Windows? Nope

9. Include the output from the following commands from Terminal.

```

ifconfig
iwconfig
route -n
ping -c 3 208.67.219.101
ping -c 3 www.opendns.com

```

I will do #9 later.


Also some questions....  How do I find out what kind of wireless card I have?  I know that I have one and that it worked back when I had Windows.  How do I make sure it is turned on?  In windows I just hit a button on my laptop.  I have done this in ubuntu and it hasn't made a difference.  Thanks for the help. ^_^

---

### Post by antikristian on 2009-04-13
First, we can gather some intel on your mothers computer:)

open the control panel, choose network connections (the names might not match completely since I'm not used to english Windows XP or have a Windows computer in front of me, but bare with me:-) )

When you get to the network connections window, there should be some icons indicating network connections, ignore the ones that are greyed out, but write down the names of the others.

In most cases there is one that is called "Local connection" or similar.

If this is the only active connection, right click it and select "properties"

In the new window that comes up, you see a white box with lots of protocols (three to six seven of them) Scroll down to the one that says TCP/IP v4, highlight it and select properties again, a new window will appear, What does it say? Automatically assigned IP addresses, or are there lots of numbers there?

Please remember to not change anything here, as it might result in loss of the network connection. Press Cancel rather than OK when exiting this window.

When you have done this, return here and let's continue.

---

### Post by shizumasa14 on 2009-04-13
[[IMG]http://img16.imageshack.us/img16/4717/91521617.th.png[/IMG]](http://img16.imageshack.us/my.php?image=91521617.png)

---

### Post by shizumasa14 on 2009-04-13
The top open window is what you told me.  Its just a bunch of empty fields.

---

### Post by antikristian on 2009-04-13
Good, That's what we were hoping for.

1. There seem two be two icons in the network connections window, what are their names? And which of them did you check the prefrences of?

2. Still on your mothers computer, press start->run 
2.1 type "cmd" and press enter
2.2 type "ipconfig /all" and press enter
2.3 look for "gateway" in the following row of text, write this down it's probably something like 192.168.0.1 or similar

Now, are you trying to connect via an ethernet cable or a wireless connection?

---

### Post by shizumasa14 on 2009-04-16
One is local area connection.  The other is 1394 connection.  I used local area connection.

ipconfig /all = 98.247.48.1

I am trying both, wireless would be nice but Ethernet is better than nothing.

---

### Post by antikristian on 2009-04-16
looks like you are getting a public ip on your mothers computer, this means that there is a limited number of IP addresses available, so you can only connect a limited number of computers.

Try to follow the network cable on your mothers computer to where it ends up and you might be so lucky that the device has several plugs/ports for network cables. If it only has one, than you need a switch, or most likely, a wireless router, or a wired router with a built in switch.

As I was about to say, if the device has available ports for a network cable, you can insert one there, connect the other end to your computer, an you will get an IP address automatically.

---

### Post by shizumasa14 on 2009-04-16
The problem is, I have even unplugged the ethernet in my moms computer and plugged it into mine, and it didn't work...

---

### Post by antikristian on 2009-04-18
some cablemodems remember the networkcard/computer it gave the last ip address to, if you have broadband through a cablemodem, you might have to unplug the power cable on this cablemodem for approx one minute and reconnect it. then remeber to have the computer or router that you want an ip address on connected to the cablemodem. to reverse the process, switch computers and do the same procedure again on the cable modem.

the best thing to do in cases like this is to buy a router/wireless router with nat (all routers aimed at the private market has this feature) this let's you connect more than one computer, and ads a pretty nice firewall which protects all the computers from intruders.

running the setup you have today with publlic accessible ip addresses on your computers running windows is potentially unsafe.

So it's a good excuse to buy a wireless router (yust remember to sue wpa encryption on the wireless) :)

---

