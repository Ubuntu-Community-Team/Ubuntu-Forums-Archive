---
title: "Cricket Wireless EC1705"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by dbodner on 2010-08-18
I've seen tutorials on the A600 and the 185, but haven't seen anything on the EC1705.  I've got this working under windows 7, but would prefer to have it working under ubuntu as well.  Anyone have this modem ?

---

### Post by theskyisdrunk on 2010-12-12
I have just purchased the Cricket Huawei EC1705 as well. I installed ubuntu and when I try to select Cricket Wireless (EVDO) from the network menu it does not work. Any suggestions?

---

### Post by ssmall on 2011-01-04
I also have this modem, it is recognized and I set up a connection, but never connects.

---

### Post by AgentWD-40 on 2011-02-21
I'm seeing the same issue here (appears in network list, but never connects). Has anybody found a resolution for this issue yet?

---

### Post by AgentWD-40 on 2011-02-21
Have any of you tried editing the connection and adding the username and password through Network Connections and then tried to connect? I'm not sure what the username and password are supposed to be for the one I'm currently working with and I can't get the owner on the phone for a bit.

---

### Post by rumphcb on 2011-03-07
I've tried everything, have spent hours, no ... days trying to get this to work, all to no avail.
 
I give up.

---

### Post by AgentWD-40 on 2011-03-07
Yeah, I had to give up as well. The machine I was working on wasn't actually mine so I told the owner that they would need to use Dial-up, DSL, or cable instead. They were paying like $30/month for that thing which should get them at least a decent DSL connection.

---

### Post by Cybrchron on 2011-03-13
I managed to get the software installed by copying it to a usb flash drive and then used wine to open it. I also followed all of the other steps to edit the username and password but now it just wont detect the modem. I have already tried to let gnome PPP detect it and still nothing. I am very new to Linux and Ubuntu so any help would be greatly appreciated.

---

### Post by Thelinuxgeek on 2011-05-21
Same problem here, too. There's no fix for this, and since it's such a lesser-known modem, i doubt Linux support will will ever be added. I'm really upset I can't go online using Ubuntu because of this.

---

### Post by alexfish on 2011-05-22
> **Thelinuxgeek said:**
> Same problem here, too. There's no fix for this, and since it's such a lesser-known modem, i doubt Linux support will will ever be added. I'm really upset I can't go online using Ubuntu because of this.
Can have a look here with a reference to usb_modeswitch 

  **[Natty, known bugs, fixes and work arounds]("http://ubuntuforums.org/showthread.php?t=1749312") ****post **#**[30]("http://ubuntuforums.org/showpost.php?p=10793568&postcount=30")**
 

 **if still not recognized can post the results of usb-devices**
 ```
usb-devices
```
 **alexfish**

---

### Post by archie1941 on 2011-06-04
Yes I have setup the username and password but like you it shows connected but only dowloads at a few bits per sec. I am starting to wonder if the thing is protected from systems other than windows????

---

### Post by Thelinuxgeek on 2011-06-15
I FIXED IT! IT'S SHOCKINGLY SIMPLE! go about setting up your broadband connection as you normally would, but set your username to [email]yourphonenumber@mycricket.com[/email]. (You can find your number by opening the connection manager in Windows, click the help tab, and then click about cricket broadband ec1705.) And then set your password to cricket. That's it! You're done! Enjoy, and I Really hope this helps you!!!

---

### Post by JoeEndUser on 2011-08-18
Just hijacking and old thread to say thanks to thelinuxgeek, I was setting up a comp for a client with mint 11 and this helped. In my case I just had to go to edit connections by clicking the network icon and editing the info in the mobile broadband tab.

Number: #777 (it was in there automagically)
user: [email]phonenumber@mycricket.com[/email] (no dashes in the phone number)
pw: cricket

---

### Post by ggarrett on 2012-07-26
I've been working on getting my newly installed ubuntu 12.04 internet access over cricket's EC1705. In network connections under broadband I'm entering my credentials 

the default is to dial #777 all the threads I've read indicate that.

My user name is my MDN full 10 digit telephone number [email]xxxxxxxxxx@mycricket.com[/email]
 
PW: cricket


I feel like I'm losing my marbles ](*,) Because it's not working. Any help would be appreciated.

---

### Post by DonGrant on 2012-10-01
I also have the Cricket Mobile Bradband EC1705.  Do you use pw as Cricket
or the pw used to access data to account to Cricket?

---

### Post by biriachan on 2012-12-17
I recently purchased this device based on the advice found on this thread. Upon receive the device and connecting it to both ubuntu 12.04 and 12.10 (and variations such as lubuntu/mint etc) and following the advice here, I found the device would not connect.

Number:     #777
Username:   [email]my10digitPhoneNumber@mycricket.com[/email] 
[ [email]9876543210@mycricket.com[/email] ]
Password:  cricket

So here's what I found.  The device **MUST **be **ACTIVATED **in either WINDOWS or MAC OS. (I did not test this on MAC, only Windows).

Pluging in the device will start a installation wizard. Once the cricket broadband software was installed I went to "Tools"->"Activation".

After that I returned to ubuntu 12.04 using the account information above and I was able to receive internet.

I hope this helps.

---

