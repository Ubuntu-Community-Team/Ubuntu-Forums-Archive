---
title: "Connecting to hidden network"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by lafferjm on 2008-12-03
I have no problems at all connecting to a network that is not hidden.  When i attempt to connect to one that is hidden without any kind of security i detect it but i am unable to connect.  I am running hardy haron and have searched for hours trying to find a solution but i can't find one.  Does one exist and i have overlooked it or am i just out of luck?  Any information that you might need are in the attachments.

---

### Post by superprash2003 on 2008-12-04
when trying to access a hidden network.. also enter an ip address with gateway ip etc . what is your wifi router's ip?

---

### Post by razy60 on 2008-12-04
if the net work is hidden your fist problem is that you need the ssid otherwise you cant even talk to the other network.(dont know if you posted those details in your post as i cant open your txt files)

Raz

---

### Post by lafferjm on 2008-12-04
@superprash2003:  I don't know the address of the router because it is located at the school.

@razy60:  I do know the ssid.

---

### Post by razy60 on 2008-12-05
In that case do you have or can you speak to whoever controls the network for the network info to enable you to connect.

Raz

---

### Post by lafferjm on 2008-12-05
I talked to network services and they said they didn't know how to do it.

---

### Post by sleepyjon on 2008-12-05
You could try this:

[Wireless Guide]("http://ubuntuforums.org/showthread.php?t=571188&highlight=wireless+command+line")

---

### Post by razy60 on 2008-12-05
they should have any and all their network details, that is unless, they are a bunch of monkeys.

if you give them your mac code they should be able to set the wireless to give you permissions to connect.
That is unless they don't actually control the network.

Raz


There are a number of threads on this forum that are dealing with a similar problem all be it worded in different way.

---

### Post by lafferjm on 2008-12-07
> **sleepyjon said:**
> You could try this:

[Wireless Guide]("http://ubuntuforums.org/showthread.php?t=571188&highlight=wireless+command+line")

That guide is for networks that are broadcasted not hidden.  I will go ahead and search around the forum a bit and see if i can't find a solution.

---

### Post by razy60 on 2008-12-07
can you connect somewhere with a Ethernet cable, get the relevant info then use that to create your wifi access.
Not ideal but it could give you the info you need,

Raz

---

### Post by skippymo on 2008-12-08
i am having this same issue, at my house with wpa-personal

if i un-hide it i can connect fine.
if hidden then i cannot.

it seems to time out and ask for credentials again and again and......

thanks

---

### Post by lafferjm on 2008-12-09
I am going to hide my connection at the house and fool around with connecting that way and see if i can't come up with a solution.

Edit:  I installed ndiswrapper and installed a driver using it and i was connecting to a hidden network at my house without any problems.  I am going to take my laptop to the school tomorrow and see if the driver was the problem.

---

### Post by skippymo on 2008-12-09
yea i have a broadcom card in my dell latitude d630, i really don't want to have to do the ndiswrapper thing still new to ubuntu and just don't feel like reading that forum post. thanks for your help.

Mike

---

### Post by lafferjm on 2008-12-10
Well as it turns out it wasn't the driver because i was unable to connect.  Would purchasing a usb adapter allow me to connect?

---

### Post by razy60 on 2008-12-10
not necessarily, you need to establish why you cant connect at school if you can connect to hidden networks at home, sounds like its a security issue with your schools network.


Raz

---

### Post by skippymo on 2008-12-10
razy60, 

seems you know a lot about ubuntu, so sorry if i am new to this.
i am a network admin and am finding out that a hidden network (wpa-personal) keeps looping the authenication. i know the credentials but to no avail. also, as soon as i un-hide this AP everything works fine. so we can get rid of security. i'm a little confused on drivers with ubuntu would this be the problem. just to test i have a netgear pcmcia card on order to see if that helps. 

thanks for your help.

---

### Post by skippymo on 2008-12-24
changed driver on my broadcom card and now it is awesome!!!!!! used the b43 driver. and can connect to hidden networks....seems to be a driver issue if you cannot connect.

thank you pytheas22 for making my life easier!

---

