---
title: "sudo apt-get remove dhcp-client (BIG PROBLEM)"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by chris.reid on 2009-10-20
I was trying to set up a static ip on my ubuntu box. 
I was following some directions online. Unfortuanately the directions were a bit out of order.
Can not find the exact ones but these are the basic instructions: (the ones I should have read)
[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)

sudo apt-get remove dhcp-client
i ran the above command before I could look up my server ip using ifconfig /all.

so I instantly lost connection to the internet. which means I cannot 
sudo apt-get install dhcp-client or run any updates.

Luckily I have this (windows) box to access the internet.

I am noob to ubuntu.
I tried restarting my network.
I have also switched the following files back to default:
/etc/network/interfaces
/etc/resolv.conf

Please help, I don't want to have to reinstall the OS again.

---

### Post by pedro_orange on 2009-10-20
Why don't you just pop onto your server / use your Windows box to find the IP address of the server?

Failing that, put the Ubuntu installation CD in your machine and just run it from the CD - so you're booting into your live CD. By default it will have a DHCP client enabled, and you'll be able to get your server's IP address.

Then you just need to set a static IP address in the same range as the servers and you're laughing.

Let us know how it goes.

---

### Post by gareththered on 2009-10-20
Have you tried to reinstall the dhcp client?

If it was in your package cache then it will be on your local computer and should reinstall.  On the other hand, if it was a fresh(ish) install and dhcp client hasn't been updated since you installed then it won't be in the cache.

Alternatively, download the dhcp-client package using server/Windows and copy (usb stick?) to your broken computer and install it.

Good luck!

---

### Post by slakkie on 2009-10-20
You might want to have a look at the following pages:

[https://help.ubuntu.com/community/NetworkConfigurationCommandLine](https://help.ubuntu.com/community/NetworkConfigurationCommandLine)

[https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)

---

### Post by dominiquec on 2009-10-20
Consider setting up a static IP address first.  

In /etc/network/interfaces, it should be something like:

iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.254

Then restart your network via sudo /etc/init.d/networking restart

---

### Post by fela on 2009-10-20
You could just download the dhcp-client deb from packages.ubuntu.com and put it on a USB memory stick. If when you removed dhcp-client, it also removed other packages (ubuntu-desktop for example), you should also get them.

---

### Post by chris.reid on 2009-10-20
Wow thanks everyone. I am so happy to have installed ubuntu and joined such a great and responsive team of people who are so willing to help others. This is fantastic.

I want to understand all of the options, so I must ask a few questions here:
Remember this is my first week of using and configuring UBUNTU.

**@gareththered** - I did try to reinstall, I used this _*sudo apt-get install dhcp-client *_. I forget the exact err msg, but it could not access the internet. I am not sure what the cache is you are talking about. Could you explain or point me in a direction to understand this better.

**@pedro_orange** - That is exactly what I did (used win to get network ip), but must not really know what number I was looking at, because nothing worked when I did it. As for the live CD method. That is good to know, I was not sure how to go about that. Also with my bios and motherboard (shuttle), I couldn't install from the cd, so had to swap hdd into my windows box and install ubuntu, then when it ask for reboot I swapped it back into my shuttle. So I was a bit worried about trying anything from the CD.

the download->usb method mentioned by a few of you. I did not know how to do this or that I could do it. I will definitely try this out next time I install something. Coming from windows, this is how everything is. I was just liking the ability for apt-get to do it all for me. hahahha

I like** dominiquec's **response because that is what I was trying to do and still would like to do.I actually did try this for an hour or two. I thought if I shuffled the numbers around enough I would surely get them some time.  I am a bit unsure about some things though. 
iface eth0 inet static
address 192.168.1.5 <- this is the static IP of the ubuntu machine and must be in the range from 100-149 (based on router settings) this may be where I messed up.
netmask 255.255.255.0 <- this I believe is OK, because I find this in my router
gateway 192.168.1.254 <- I will have to look up these numbers?

---

### Post by chris.reid on 2009-10-20
Whoops I made a huge mistake when I posted this response. I think I actually used this to remove the client or whatever it did. 

[SIZE=4]**sudo update-rc.d -f NetworkManager remove**[/SIZE]

It was late last night and once I did the deletion, I had to use my windows machine to find the article I was using to do the static ip. And I am pretty sure I copied and pasted this into the command line. 

Should I start a new thread for this. or keep going on this one.

---

### Post by slakkie on 2009-10-20
> **chris.reid said:**
> Whoops I made a huge mistake when I posted this response. I think I actually used this to remove the client or whatever it did. 

[SIZE=4]**sudo update-rc.d -f NetworkManager remove**[/SIZE]

It was late last night and once I did the deletion, I had to use my windows machine to find the article I was using to do the static ip. And I am pretty sure I copied and pasted this into the command line. 

Should I start a new thread for this. or keep going on this one.

Easy to fix:

```
sudo update-rc.d -f NetworkManager defaults
```

And then you should be good to go.

---

### Post by chris.reid on 2009-10-20
Looks like this may work.
[http://ubuntuforums.org/archive/index.php/t-632179.html](http://ubuntuforums.org/archive/index.php/t-632179.html)

Man, removing kernels (this is starting to sound bad).

Is this recommended? I guess everyone has to learn some way or another. I am sure you guys had to reinstall linux a couple times to get your knowledge. I guess I should try it.

---

### Post by chris.reid on 2009-10-20
after some research, this seems like it is for wireless. I dont have wireless so I will not do it.

---

### Post by chris.reid on 2009-10-20
[B][SIZE=4][------------SOLVED HERE-------------][/SIZE]

@Slakkie[/B]

```
sudo update-rc.d -f NetworkManager defaults
```
Thanks a million. ran the above line
I tried to /etc/init.d/network restart and it didn't fix it, but when I restarted everything worked perfectly. Thanks

---

### Post by gareththered on 2009-10-20
Glad you got it fixed!!

For your information, packages are cached in '/var/cache/apt/archives' (have a look at yours) when they are downloaded from the Internet (but not when originally installed from the install CD).  If you remove something that's been installed from the Internet then you can re-install with no Internet access as apt-get or synaptic etc will look in the cache first before downloading from the Internet.

Regards.

---

### Post by fela on 2009-10-20
Great, now let this be a lesson to always know exactly what a command does and how to reverse the consequences before you go pasting it into a terminal. The Linux terminal is a mighty powerful thing, and it can be misused.

---

