---
title: "two seperate, possibly related problems"
date: 2012-07-19
forum: Mythbuntu
---

### Post by DrewLGT on 2012-07-19
I just finished building my first HTPC, and installed mythbuntu. I'm having some problems....

In the initial setup, Im a little confused about setting up my HDHomerun tuner. I pick the HDHR from the drop down menu at the top, but Im unsure what i need to put in the IP address field.  the tuner is hooked directly to the computer via an ethernet cable.

The other problem Im having is that when i start the front end, i get an error message that says it was unable to connect to the backend. I have verified that the backend is running, and since i'm using one machine as the front/backend I'm using the loopback IP address.  I think it might be a password/sql issue, not really sure what to do here....

---

### Post by dewmanstl on 2012-07-19
Your HDHR is plugged into the PC via a Network cable?

---

### Post by DrewLGT on 2012-07-19
> **dewmanstl said:**
> Your HDHR is plugged into the PC via a Network cable?

That's right...

---

### Post by 921mary on 2012-07-19
Awesome!!!!:o

---

### Post by DrewLGT on 2012-07-19
> **921mary said:**
> Awesome!!!!:o

:confused:

---

### Post by dewmanstl on 2012-07-19
The HDHR needs to be plugged into a switch since its a network device. Best bet would be to probably (and people can correct me here) would be to give the ip address of your FE/BE a static address, that way you dont have to worry about DHCP handing it a different address each time it reboots or you restart networking. Then I would follow this guide
[http://www.mythtv.org/wiki/User_Manual:Utilities_and_Setup#Setup](http://www.mythtv.org/wiki/User_Manual:Utilities_and_Setup#Setup)

I think once you get the FE/BE a IP address it should start to come together for you. :)

---

### Post by dewmanstl on 2012-07-19
> **dewmanstl said:**
>  Best bet would be to probably (and people can correct me here) would be to give the ip address of your FE/BE a static address, that way you dont have to worry about DHCP handing it a different address each time it reboots or you restart networking.. :)

I forgot to mention that you will want to plug your FE/BE into the same switch as well.

---

### Post by nickrout on 2012-07-20
Actually the HDHR can be plugged in with a crossover cable without a switch or hub. 

You are best to specify the HDHR by ID rather than IP address.

---

### Post by DrewLGT on 2012-07-20
> **nickrout said:**
> Actually the HDHR can be plugged in with a crossover cable without a switch or hub. 

You are best to specify the HDHR by ID rather than IP address.


the HDHR docs say a crossover cable isnt needed....


it also says it needs a 169.254.x.x ip address. i tried 169.254.1.1, still didnt work

---

### Post by DrewLGT on 2012-07-20
I actually tried both the numbers on the bottom of the HDHR. The id and the Mac address...

---

### Post by tgm4883 on 2012-07-20
It says to set your PC to a 169.254 address to speed up the time it takes the PC to find it. What this is really doing is just eliminating the timeout of DHCP on your PC. So make sure that is set.

You need to fire up the hdhomerun_config_gui (apt-get install hdhomerun-config-gui) application and see if the PC even detects the HDHomerun device that is connected. Then you can even use it to tune a channel and see if it's working correctly.

---

### Post by DrewLGT on 2012-07-20
> **tgm4883 said:**
> It says to set your PC to a 169.254 address to speed up the time it takes the PC to find it. What this is really doing is just eliminating the timeout of DHCP on your PC. So make sure that is set.

You need to fire up the hdhomerun_config_gui (apt-get install hdhomerun-config-gui) application and see if the PC even detects the HDHomerun device that is connected. Then you can even use it to tune a channel and see if it's working correctly.

That program is actually built into mythbuntu now.... It doesn't detect the tuner

---

### Post by DrewLGT on 2012-07-20
> **tgm4883 said:**
> It says to set your PC to a 169.254 address to speed up the time it takes the PC to find it. What this is really doing is just eliminating the timeout of DHCP on your PC. So make sure that is set.



Where do I need to set the IP for the tuner? In mythtv somewhere, or in the network settings in mythbuntu? I tried changing the network settings in mythbuntu, and I don't have permission.

---

### Post by tgm4883 on 2012-07-20
> **DrewLGT said:**
> Where do I need to set the IP for the tuner? In mythtv somewhere, or in the network settings in mythbuntu? I tried changing the network settings in mythbuntu, and I don't have permission.

You don't set the IP of the tuner, because you don't know the IP of the tuner. Not puting this on your regular network is causing some issues. You may want to (at least temporarly) put it on your regular network so you can A) verify it's working and B) configure it (which I'm assuming you can do with the original, as I only have an HDHR Prime)

---

### Post by DrewLGT on 2012-07-20
> **tgm4883 said:**
> You don't set the IP of the tuner, because you don't know the IP of the tuner. Not puting this on your regular network is causing some issues. You may want to (at least temporarly) put it on your regular network so you can A) verify it's working and B) configure it (which I'm assuming you can do with the original, as I only have an HDHR Prime)



The only reason it isn't on the network already is because I have an old 54mbs router, and the HTPC is half way across the house. Will I be able to stream HD content?

---

### Post by tgm4883 on 2012-07-20
> **DrewLGT said:**
> The only reason it isn't on the network already is because I have an old 54mbs router, and the HTPC is half way across the house. Will I be able to stream HD content?

It won't wirelessly, that isn't fast enough. But you would be able to configure it and verify that it works. IIRC, you can set the IP address of it in the web settings.

---

### Post by DrewLGT on 2012-07-20
> **tgm4883 said:**
> It won't wirelessly, that isn't fast enough. But you would be able to configure it and verify that it works. IIRC, you can set the IP address of it in the web settings.

I'm sorry to be such a noob, but I can put it on the network, assign it an IP, then hook it back up to my PC and plug that IP into the mythtv settings?

---

### Post by tgm4883 on 2012-07-20
> **DrewLGT said:**
> I'm sorry to be such a noob, but I can put it on the network, assign it an IP, then hook it back up to my PC and plug that IP into the mythtv settings?

I just looked at mine, and apparently that isn't an option. If you only have the one HDHomerun, try using the device ID FFFFFFFF in MythTV

---

### Post by DrewLGT on 2012-07-20
> **tgm4883 said:**
> I just looked at mine, and apparently that isn't an option. If you only have the one HDHomerun, try using the device ID FFFFFFFF in MythTV

Thanks for the suggestion. the only option under the HDHR setup in mythtv is for an IP address. Put eight f's there?

If this doesn't work, what is the preferred pci tuner for mythtv? If I have to put the HDHR on the network its going to cause me more trouble than its worth.

---

### Post by DrewLGT on 2012-07-20
The F's didn't work...

---

### Post by tgm4883 on 2012-07-20
> **DrewLGT said:**
> The F's didn't work...

Do you have a firewall on?

---

### Post by DrewLGT on 2012-07-20
> **tgm4883 said:**
> Do you have a firewall on?

No, I just bought a hauppage hvr-1250. I was never crazy about the idea of an external tuner, but it was free.

---

### Post by nickrout on 2012-07-21
shame, the hdhr is much better!

---

### Post by DrewLGT on 2012-07-21
> **nickrout said:**
> shame, the hdhr is much better!



How so?

---

### Post by nickrout on 2012-07-21
> **DrewLGT said:**
> How so?

Very reliable, not reliant on drivers that may work with this kernel, but not with that kernel, enabes you to put your backend in a physically separate position from where you antenna cable terminates, has two tuners, good support from the manufacturer, works out of the box with mythtv.

---

### Post by johnvic on 2012-07-22
I have the hdhmerun. You cannot assign a static ip address to hdhr, your router must assign it. I programmed my router to reserve a specific ip address to the hdhr. I'm not sure if I needed to do this but I prefer to have devices have static ip addresses. 

When you set up the backend for tuners you will choose hdhomerun in card type, then move to the device number, just right arrow and it will show the hadhomerun on your network. You will find 2 devices and when you go to add the second tuner it will show the first device as already being used.

---

### Post by anonymousdog on 2012-07-22
> **johnvic said:**
> I have the hdhmerun. You cannot assign a static ip address to hdhr, your router must assign it. I programmed my router to reserve a specific ip address to the hdhr. I'm not sure if I needed to do this but I prefer to have devices have static ip addresses. 

When you set up the backend for tuners you will choose hdhomerun in card type, then move to the device number, just right arrow and it will show the hadhomerun on your network. You will find 2 devices and when you go to add the second tuner it will show the first device as already being used.

So, if that's true, the OP, to get this to work, would need to configure on an AutoIP address the NIC to which the HDHR is connected (preferably a "high" one so the HDHR doesn't try selecting the same IP).  This is absolutely required or IP communications with the HDHR simply won't work (regardless of referencing the device by device number).  He seems to have ignored the previous instruction to do so, preferring to attend to the MythTV BE's setup screens prompting for an HDHR IP address (instead of addressing his having not assigned the BE's NIC a static IP).

Drew, if you give up on the HDHR, feel free to send it to me ;)

---

### Post by DrewLGT on 2012-07-22
> **anonymousdog said:**
> So, if that's true, the OP, to get this to work, would need to configure on an AutoIP address the NIC to which the HDHR is connected (preferably a "high" one so the HDHR doesn't try selecting the same IP).  This is absolutely required or IP communications with the HDHR simply won't work (regardless of referencing the device by device number).  He seems to have ignored the previous instruction to do so, preferring to attend to the MythTV BE's setup screens prompting for an HDHR IP address (instead of addressing his having not assigned the BE's NIC a static IP).

Drew, if you give up on the HDHR, feel free to send it to me ;)


Im sorry, are you saying that i can use the HDHR without putting it on the network?


please break that down for me

---

### Post by johnvic on 2012-07-22
You need a router to use the hdhr, not just a switch. The router must assign ip addresses.

---

### Post by tgm4883 on 2012-07-23
> **johnvic said:**
> You need a router to use the hdhr, not just a switch. The router must assign ip addresses.

That isn't 100% true. He could setup a DHCP server on his backend and have it listen on the wired interface.

---

### Post by nickrout on 2012-07-23
> **tgm4883 said:**
> That isn't 100% true. He could setup a DHCP server on his backend and have it listen on the wired interface.

Or you could let the backend and the HDHR get 169.* zeroconf IP addresses, but this isn't an option if you have other devices on your LAN - in which case you will need proper IP addresses. Best set up that way from the start.

---

### Post by DrewLGT on 2012-07-23
> **nickrout said:**
> Or you could let the backend and the HDHR get 169.* zeroconf IP addresses, but this isn't an option if you have other devices on your LAN - in which case you will need proper IP addresses. Best set up that way from the start.


this all way over my head, it's making me feel stupid :(

for real though, if anyone would like to purchase this HDHomeRun, PM me with an offer

---

### Post by nickrout on 2012-07-24
You are in the USA? (There are different models for different markets)

---

### Post by DrewLGT on 2012-07-24
> **nickrout said:**
> You are in the USA? (There are different models for different markets)

I am...

---

