---
title: "what is my current WIFI password"
date: 2011-10-08
forum: Networking &amp; Wireless
---

### Post by itcave on 2011-10-08
Ubuntu 10.10
How do I find the WIFI password of my current connection?  I didn't save it using the password manager and it's not showing up in the networkmanager settings screen.  I'm connected now, so there has to be a way in terminal to lookup my current password....  right?

Thanks for your help!

---

### Post by roger_1960 on 2011-10-08
Hi

Click on the network icon at top right.

Select "edit connections"

Select the "wireless" tab and then select the current connection.

Select "edit".  Select the "wirelesss security" tab and finally click the "show password" box.

(Then close everything with no changes)

Bit longwinded but I don't know another way.

Roger

---

### Post by itcave on 2011-10-08
> **roger_1960 said:**
> Hi

Click on the network icon at top right.

Select "edit connections"

Select the "wireless" tab and then select the current connection.

Select "edit".  Select the "wirelesss security" tab and finally click the "show password" box.

(Then close everything with no changes)

Bit longwinded but I don't know another way.

Roger
Thanks for the reply Roger. I actually already tried this.  When I go follow your instructions the password box is blank.  I think this may be because I didn't save the password with the password manager. 

Does anyone know another way to check the password for your current WIFI connection?

Thanks

---

### Post by thefasterblueone on 2011-10-08
Try looking in:

```
sudo cat /etc/NetworkManager/system-connections/[COLOR="Red"]YOUR-SSID[/COLOR]
```

---

### Post by roger_1960 on 2011-10-08
Could it be a blank password?  You could use this method to change it to something new that you know.

---

### Post by itcave on 2011-10-08
> **thefasterblueone said:**
> Try looking in:

```
sudo cat /etc/NetworkManager/system-connections/[COLOR="Red"]YOUR-SSID[/COLOR]
```

I get the following error when I run that:

cat: /etc/NetworkManager/system-connections/The_A-TEAM: No such file or directory

---

### Post by thefasterblueone on 2011-10-08
If your connection is set to connect automatically you will need to add 'Auto' to the command.

Try adding the 'Auto', like:

```
sudo cat /etc/NetworkManager/system-connections/Auto\ The_A-TEAM 
```

---

### Post by itcave on 2011-10-08
> **thefasterblueone said:**
> Try adding the 'Auto', like:

```
sudo cat /etc/NetworkManager/system-connections/Auto\ The_A-TEAM 
```

still no luck

cat: /etc/NetworkManager/system-connections/Auto The_A-TEAM: No such file or directory

---

### Post by thefasterblueone on 2011-10-08
Are you using 'sudo' in the command ?

Are you using Network manager or WICD ?

---

### Post by haqking on 2011-10-08
passwords and encryption keys, your passwords, find your wireless connection listed, properties and choose show password

also if you are connected and it is your connection then login to your router and see what it is, if not your connection then ask the person whose connection it is to tell you if you are supposed to be connected ;-)

---

### Post by itcave on 2011-10-08
> **thefasterblueone said:**
> Are you using 'sudo' in the command ?

Are you using Network manager or WICD ?


Yes I'm using sudo

I am using network manager

---

### Post by haqking on 2011-10-08
> **itcave said:**
> Yes I'm using sudo

I am using network manager

if you are connected why dont you just login to your device to see what it is ?

---

### Post by itcave on 2011-10-08
> **haqking said:**
> if you are connected why dont you just login to your device to see what it is ?

I am connected.  It's my neighbors WIFI.  I'm having trouble with my service so he let me use his.  He typed in the password on my pc.  I'm trying to connect a second pc, but I don't have the password.  I would ask the neighbor again, but he just left for a 2 week vacation.

---

### Post by haqking on 2011-10-08
> **itcave said:**
> I am connected.  It's my neighbors WIFI.  I'm having trouble with my service so he let me use his.  He typed in the password on my pc.  I'm trying to connect a second pc, but I don't have the password.  I would ask the neighbor again, but he just left for a 2 week vacation.

ha ha mmmmmmmm sounds dodgy to me ;-)

Use your passwords and encryption keys i mentioned earlier

it must be saved, otherwise you wouldnt of reconnected to it, unless it has never disconnected since he went on vacation ;-)

---

### Post by itcave on 2011-10-08
> **haqking said:**
> ha ha mmmmmmmm sounds dodgy to me ;-)

Use your passwords and encryption keys i mentioned earlier

it must be saved, otherwise you wouldnt of reconnected to it, unless it has never disconnected since he went on vacation ;-)

It is not in the Passwords and Encryption Keys.  Your right I haven't disconnected since he went on vacation.

---

### Post by haqking on 2011-10-08
> **itcave said:**
> It is not in the Passwords and Encryption Keys.  Your right I haven't disconnected since he went on vacation.

so the current connection you are connected to does not show up in network manager when you choose to edit connections and the keyring is not in your keyring folder ?

---

### Post by roger_1960 on 2011-10-08
Ha

Perhaps the neighbour ticked the "ask for passphrase evey time" box when he signed in!

---

### Post by itcave on 2011-10-08
> **haqking said:**
> so the current connection you are connected to does not show up in network manager when you choose to edit connections and the keyring is not in your keyring folder ?

It does show up in network manager when I choose edit connections, but the password field is blank.  Even when I check, 'show password' it is still blank.  

No it is not in the Encryption Key Manager.

---

### Post by itcave on 2011-10-08
> **roger_1960 said:**
> Ha

Perhaps the neighbour ticked the "ask for passphrase evey time" box when he signed in!

You may be right.  Still, there must be some why to get at the password somehow.  It has to be known somewhere, otherwise I wouldn't be connected right now.

---

### Post by haqking on 2011-10-08
> **itcave said:**
> You may be right.  Still, there must be some why to get at the password somehow.  It has to be known somewhere, otherwise I wouldn't be connected right now.

do you have another device you can use ? i reckon it might be a blank password or phrase.

or in network connections on the current connection tick the box which says connect automatically and should store it unless they asked for it it be asked for each time

---

### Post by itcave on 2011-10-08
> **haqking said:**
> do you have another device you can use ? i reckon it might be a blank password or phrase.

or in network connections on the current connection tick the box which says connect automatically and should store it unless they asked for it it be asked for each time

I do have another device to test it with.  Blank doesn't work and it's WPA2 encryption.  I have checked the 'connect automatically' box, but afraid to disconnect to try it out in case it doesn't work.

---

### Post by haqking on 2011-10-08
> **itcave said:**
> I do have another device to test it with.  Blank doesn't work and it's WPA2 encryption.  I have checked the 'connect automatically' box, but afraid to disconnect to try it out in case it doesn't work.

mmm so you are sure it wasnt in passwords and encryption keys, in the folder for my passwords you need to click it to drop it down incase you didnt know.

---

### Post by thefasterblueone on 2011-10-08
> **itcave said:**
> I am connected.  It's my neighbors WIFI.  I'm having trouble with my service so he let me use his.  He typed in the password on my pc.  I'm trying to connect a second pc, but I don't have the password.  I would ask the neighbor again, but he just left for a 2 week vacation.

You say you are "having trouble with my service", If you are a paying customer contact customer support and get it fixed.

---

### Post by haqking on 2011-10-08
> **thefasterblueone said:**
> You say you are "having trouble with my service", If you are a paying customer contact customer support and get it fixed.

edit: misread

---

### Post by itcave on 2011-10-08
> **haqking said:**
> mmm so you are sure it wasnt in passwords and encryption keys, in the folder for my passwords you need to click it to drop it down incase you didnt know.

I'm sure.  It had the passwords for 3 other WIFI connects that I have made in the past, but not for the current one.

---

### Post by CharlesA on 2011-10-08
Best thing to do would be to ask your neighbor. If they are on vacation, just deal with it until they got back or get your service fixed.

---

