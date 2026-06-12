---
title: "Have to type password on each boot"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by Sirupsen on 2009-10-31
Hello there!

When I'm using Wireless, I have to type in a password before it connects to the internet. If I connect with wire, it connects - but I still have to type in the password. It's annoying I have to do this on each boot, is there any way to fix this, or is it some kind of security thing?

---

### Post by Earl-Grey on 2009-10-31
I have a similar problem, I was just going to write a new thread but you already started this one :p

                                 



 I can use the internet but when I reboot my machine it does not connect automatically to my wireless network. I can see it trying to connect but it seemingly times out and say that it could not connect.


 When I go to the network manager I can see that all of the information is correct including my password. So I try again to connect and nothing.


 Next I check the network manager again, and suddenly the text box where my password was before is blank. So I try typing it in again. It try to connect but no luck.


 The only way I know how to get it to work is by deleting all the information I had previously typed in and starting again. After typing in the new network settings and password (WEP keys) it works fine again.


 So, I am really happy that I can get the internet to work, but does anybody know how I can fix this problem so I don't have to keep typing my network profile every time I reboot. :-k

---

### Post by majocanada on 2009-10-31
I've had the SAME issue for some time. Not only does it ask me for the Password for a particular wireless router, after I enter it, I then get a pop-up screen telling me that a file requires my Password. When I enter that, it just keeps asking me for the same thing over & over. After the second request, I just X it out without putting in my password and ~ the wireless connection IS ESTABLISHED. !
The next time I turn my computer on, I have to go through all that process again ~ no matter what I've stored in the Wireless connections.

I've learned to live with it BUT ~ there's got to be a better way ??!

---

### Post by Sirupsen on 2009-10-31
> **majocanada said:**
> 
I've learned to live with it BUT ~ there's got to be a better way ??!

Exactly! I hope some of the Ubuntu guros can help us out. :)

---

### Post by Earl-Grey on 2009-10-31
I am sure that it is something really simple that we are overlooking. :shock:



I tried deleting the default network manager and installing a different one, but I couldn't get that to work. I deleted the newer program and now I have no network manager at all :o

I can't download the network manager I was using in the first place as I can't connect to the internet without any network programs.

I've had to go back to using XP at the moment. Does anbody know how to get the network manager software back or a similar program?

---

### Post by Earl-Grey on 2009-11-02
Just wondering has anybody solved this problem yet? Everytime I use Ubuntu it doesn't connect to my wirelesss network automatically, so I have to type in my network information.

It wouldn't be that bad if it look a few seconds but it takes quite a long time to type in my networks name and passwords. 

When I reboot my settings are still saved but it doesn't connect. So I have to delete my previous settings, log off and type them in again. After this I get a 90% chance of it working.

If anybody could offer any advice I would be very greatful.

---

### Post by readycarpenter on 2010-03-31
this is a security issue, all passwords are saved in the users "keyring", such as your wireless key, at boot-up the system wants to access your keyring to get the wireless password which is encrypted in the keyring. that is why you have to put in the user password, not the wireless password, read about keyrings

---

### Post by Earl-Grey on 2010-03-31
> **readycarpenter said:**
> this is a security issue, all passwords are saved in the users "keyring", such as your wireless key, at boot-up the system wants to access your keyring to get the wireless password which is encrypted in the keyring. that is why you have to put in the user password, not the wireless password, read about keyrings

Thanks for the reply.

I think I have a slightly different problem though. I only have to type my user password when I log in after a restart. 

The internet icon swirls around trying to connect and they just shows the ||| straight lines to say it hasn't connected. When I go into the network manager, I can see the settings have saved where I typed in my network information. However my long wepkey password box is empty, so I have to type in my password information again.

After typing it in again it works about 1% of the time. I normally have to keep typing it in to the network manager and after a few hours it works.

---

### Post by sbraz on 2011-07-27
about your password requests there might be something wrong about your keyring so you all might want to try this:

[COLOR="Red"]**unsafe way** "rm ~/.gnome2/keyrings/*"[/COLOR]
[COLOR="Blue"]**safer way** "mv ~/.gnome2/keyrings ~/.gnome2/keyrings-backupjustincase"[/COLOR]

the unsafe way DELETES stuff, be careful. both commands will delete all your stored passwords and you'll have to choose a new keyring password (or no password at all if you wish)

more about keyrings
[http://nullroute.eu.org/~grawity/gnome-keyring-autologin.html](http://nullroute.eu.org/~grawity/gnome-keyring-autologin.html)

> **Earl-Grey said:**
> I tried deleting the default network manager and installing a different one, but I couldn't get that to work. I deleted the newer program and now I have no network manager at all :o

I can't download the network manager I was using in the first place as I can't connect to the internet without any network programs.

I've had to go back to using XP at the moment.

been there, done that. :D

assuming that you haven't deactivated the dhcp server in your modem, connect an ethernet cable then try "sudo dhclient". this usually works for me.
to reinstall the network manager i think it's something like "sudo apt-get install network-manager-gnome".

---

### Post by sbraz on 2011-07-27
LOL i just noticed the date sorry for hardcorenecroexhuming, i've arrived here when i read Earl-Grey's sign. :D

> If anybody can help me out with my network problem I would be very grateful. 
Please click &#8594; Here &#8592;

---

### Post by lisati on 2011-07-27
Old thread closed so it can rest.

---

