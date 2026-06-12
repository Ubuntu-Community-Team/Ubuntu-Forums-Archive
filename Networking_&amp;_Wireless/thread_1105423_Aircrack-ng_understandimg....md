---
title: "Aircrack-ng understandimg..."
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by scrypt on 2009-03-24
He/All

I'm interested in finding out how secure or insecure a wep protected network is of mine?

I want to learn about Networks, and more to the point network security,
Seeing as I will be helping set up a network for my family business.

I am using Ubuntu 8.10 and I have installed aircrack-ng.

I am still a relatively new to ubuntu so I thought that learning to use aircrack would be a good way to learn about my own network vulnerabilities.

I also understand that I should be using WPA enryption when i finally start using my Network.

I  want to learn how to find the WEP password for one of my own Routers simply for learning processes?

My wireless card is A Dell 1737 with a broadcom wireless card.
So I know it is compatible with using aircrack-ng.

This leads me to my main question....

Can anyone help me to understand how I can Find out the wep password of one of my routers? using aircrack-ng?

and is there a gui I can use to maybe simplify the process?

Im also hoping maybe someone has actually done this themselves and can even help me to do the above??

I look forward to all replies and input.

Thank's in advance

scrypt...

---

### Post by WrathofthePenguin on 2009-03-25
> **scrypt said:**
> He/All

I'm interested in finding out how secure or insecure a wep protected network is of mine?

I want to learn about Networks, and more to the point network security,
Seeing as I will be helping set up a network for my family business.

I am using Ubuntu 8.10 and I have installed aircrack-ng.

I am still a relatively new to ubuntu so I thought that learning to use aircrack would be a good way to learn about my own network vulnerabilities.

I also understand that I should be using WPA enryption when i finally start using my Network.

I  want to learn how to find the WEP password for one of my own Routers simply for learning processes?

My wireless card is A Dell 1737 with a broadcom wireless card.
So I know it is compatible with using aircrack-ng.

This leads me to my main question....

Can anyone help me to understand how I can Find out the wep password of one of my routers? using aircrack-ng?

and is there a gui I can use to maybe simplify the process?

Im also hoping maybe someone has actually done this themselves and can even help me to do the above??

I look forward to all replies and input.

Thank's in advance

scrypt...

I do this all the time. However, keep in mind that my career involves network security, so I have a reason to do it. I also do it for friends to show them why their WEP encrypted wireless network is not safe. DO NOT start cracking networks for the fun of it. I debated whether or not to post this, but since the information is so freely available (such as in the man pages) there's no point in avoiding it. Security through obscurity is NOT security.

First, understand that aircrack-ng is actually several tools. My personal favorites are airodump-ng, aireplay-ng and aircrack-ng.

Second, you can crack a network either actively or passively. Passively is legal (at least where I am), as you are only capturing packets. You can then attempt to figure out the key later. Active means you actually interact with the network, such as with aireplay-ng. Aireplay-ng allows you to attack the network in various way. I prefer the arp replay attack.

airodump-ng will take packets that are captured and write them to a file.

Here's an example of a command I'd run to start a capture:

> sudo airodump-ng --ivs -w crackfile --bssid 00:18:01:FB:FE:6E --channel 11 eth1

This will capture all packets received on eth1 (--ivs means it just saves the packets useful for cracking) to a file named crackfile (in the directory you run the command from) for the network with the specified bssid. I add the channel because otherwise it will cycle through channels and if I'm after one particular network there's no point cycling through the channels. If you don't know the bssid simply do the command:

> sudo airodump-ng eth1

to list the networks/bssids/channels etc.

Use of aireplay-ng causes more packets to be generated, so more ivs packets are generated.

An example of a command I would use for the above network would be:

sudo aireplay-ng -a 00:18:01:FB:FE:6E --arpreplay eth1

This would perform an arpreplay attack on the specific bssid on the eth1 interface.

Once you feel you've collected enough packets, you can stop both and use aircrack-ng to make an attempt to crack the key. The more packets you've captured the faster it will be cracked. I've had situations in which I've captured so many packets that cracking the key took less than 10 seconds.

For the above file (crackfile), I'd use the command:

> sudo aircrack-ng crackfile.ivs crackfile2.ivs 

Notice that I've put two filenames in the command. This is because there have been times I've captures with airodump-ng several times. The files are named sequentially and can all be specified for use in a crack attempt in the same command.

I've left out a lot of the different possibilities - the suite has a lot of different options, many of which I simply don't use.

WOTP

---

### Post by scrypt on 2009-03-26
Hi

Thank-you for your reply. Ver isightful

are you free I would like to ask you a couple of questions??

if that is okay??

---

### Post by cma37 on 2009-04-26
Thank you- thank you

---

