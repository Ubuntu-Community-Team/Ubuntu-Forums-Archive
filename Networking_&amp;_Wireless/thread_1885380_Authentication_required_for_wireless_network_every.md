---
title: "Authentication required for wireless network every time I logon"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by chesl73 on 2011-11-23
Hi,
Just installed Ubuntu 11.10 for the first time and all looking good except for one small annoying problem.
Everytime I logon or the laptop returns from suspend it seems to take a while to reconnect to the wireless network (any way of speeding this up?) and then I'm given a prompt saying 'Authentication required by wireless network' and there is a Password box which is already filled in with my wireless network password. All I have to do is click the 'Connect' button without typing anything in and then it connects. There isn't anything wrong with my wireless network as my work laptop with Windows7 connects fine. 
I've gone into Edit Connections and clicked 'Available to all users' etc but it doesn't make any difference. 
 
It seems like a fairly basic thing to have working, not sure why it isn't.
 
Any ideas how to stop it prompting me?
 
Thanks.

---

### Post by 73ckn797 on 2011-11-23
I assume you have also set it to connect automatically? That should be on the same window where you allow all users.

---

### Post by chesl73 on 2011-11-23
[SIZE=2]Yes, the automatically connect is clicked.
It does automatically try to connect but it just prompts me every time for the password even though the password is actually saved in the dialog box. It's a bit odd.
[/SIZE]

---

### Post by matsmohlin on 2011-11-29
I just want to add that I see the same problem since I upgraded to Ubuntu 11.10.
From my userid (with rooot authority) I need to enter the wireless password evyry time I login 
Another userid at the same system (with no root authority) does not see this problem.
I am no linux expert but I have in this area not changed anything.
I regularly run Update Manager and this made me upgrade to 11.10 and 11.10 works OK apart from this
annoying feature.
Mats Mohlin Sweden

---

### Post by Steve Hayes on 2011-12-14
Same problem here with 11.10 on an HP dm1 (Ralink 5390 wireless if I remember right), Draytek router and WPA. After a cold start, it occasionally connects right away but usually throws up the Authentication required box (with the password already correctly set) once or twice. There's a long delay each time. Eventually it connects correctly.

However, if the machine is suspended (even during one of the long delays), the wireless always connects immediately on resumption.

Methinks it's a timing problem related to the delay before the keyring is unlocked after cold-start along with bugs in the driver where things aren't properly initialised before each connection retry. I do have "Available to all users" checked but don't have a second user on the machine to try out.

---

### Post by Johnny English on 2011-12-30
I'm having the same problem since upgrading to 11.10 from 10.04. Stupidly, I also replaced my wireless adapter at the same time (my old D-Link DW130 never worked) so I've introduced a second variable, but I'm sure it's an issue of the OS rather than the device as I didn't install any drivers.

I've done a bit of hunting around and found this:

[http://askubuntu.com/questions/85781/wireless-authentification-appears-even-when-wep-key-is-saved](http://askubuntu.com/questions/85781/wireless-authentification-appears-even-when-wep-key-is-saved)

The answer is fairly unhelpful, especially to a not particularly technical person such as I, but can anyone tell me if it is at least on the right lines? If the issue is with Gnome Keyring, will disabling that service cause issues elsewhere? The authentication bug is annoying (I came down this morning to find about 30 of those pop ups requesting the key needed clearing), but it doesn't seem to be actually disabling the wireless service.

---

### Post by csaveanu on 2012-01-30
Maybe this thread indicates a solution:
[http://ubuntuforums.org/showthread.php?t=1424085]("http://ubuntuforums.org/showthread.php?t=1424085")

If you don't want to follow the link - what it says is that there is an option, when editing a wireless profile connection, called "Available to all users" that you can activate. Activating this option might solve the annoying problem of having at each login a window asking to push the OK button.

---

### Post by gatesdrovme2it on 2012-02-02
I have tried the options discussed here but no luck.  This problem just popped up for me- my Lenovo has been a dream with Ubuntu 11.10 until today.  Is this a bug in the O/S?  There are other threads about it but nothing solves the problem.

---

### Post by gatesdrovme2it on 2012-02-03
Anyone?  Any ideas at all?

---

### Post by raja.genupula on 2012-02-03
> **chesl73 said:**
> Hi,
Just installed Ubuntu 11.10 for the first time and all looking good except for one small annoying problem.
Everytime I logon or the laptop returns from suspend it seems to take a while to reconnect to the wireless network (any way of speeding this up?) and then I'm given a prompt saying 'Authentication required by wireless network' and there is a Password box which is already filled in with my wireless network password. All I have to do is click the 'Connect' button without typing anything in and then it connects. There isn't anything wrong with my wireless network as my work laptop with Windows7 connects fine. 
I've gone into Edit Connections and clicked 'Available to all users' etc but it doesn't make any difference. 
 
It seems like a fairly basic thing to have working, not sure why it isn't.
 
Any ideas how to stop it prompting me?
 
Thanks.

Hi please give me the output of  ```
iwconfig
```.

Thank you .

---

### Post by gatesdrovme2it on 2012-02-03
Raja will you look at mine also please?

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

---

### Post by dix1040 on 2012-02-03
> **chesl73 said:**
> Hi,
Just installed Ubuntu 11.10 for the first time and all looking good except for one small annoying problem.
Everytime I logon or the laptop returns from suspend it seems to take a while to reconnect to the wireless network (any way of speeding this up?) and then I'm given a prompt saying 'Authentication required by wireless network' and there is a Password box which is already filled in with my wireless network password. All I have to do is click the 'Connect' button without typing anything in and then it connects. There isn't anything wrong with my wireless network as my work laptop with Windows7 connects fine. 
I've gone into Edit Connections and clicked 'Available to all users' etc but it doesn't make any difference. 
 
It seems like a fairly basic thing to have working, not sure why it isn't.
 
Any ideas how to stop it prompting me?
 
[SIZE=3]Thanks.[/SIZE][SIZE=3]
Well I'm glad you asked, it's a very simple fix. Just click on the cancel button until prompted for your wireless network security key after entering your wireless key then click connect. Of course you will be prompted to put in the keyring password but just click on the cancel button and you will then notice that your Internet connection is established and connected. So to eliminate being asked for the keyring all together. click on the system icon, once in the system settings click on the password and encryption key icon once in there you will need to delete the default password settings. Once thats done goodbye to that problem for good. 
let me know how you made out OK.
dix1040[/SIZE]

---

### Post by gatesdrovme2it on 2012-02-03
Dix1040 is a troll

---

### Post by dix1040 on 2012-02-03
> **gatesdrovme2it said:**
> Dix1040 is a troll

why do you say that (troll)?

---

### Post by gatesdrovme2it on 2012-02-04
"[SIZE=3]Just click on the cancel button until prompted for your wireless network security key"

-impossible.  it never happens.
[/SIZE]
[SIZE=3]"[/SIZE][SIZE=3]click on the system icon, once in the system settings click on the password and encryption key icon"

-impossible.  there is no such icon and you know it.

go away, troll
[/SIZE]

---

### Post by raja.genupula on 2012-02-04
> **gatesdrovme2it said:**
> Raja will you look at mine also please?

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

please explain your problem , aah! it always better to start a new thread for more help.

---

### Post by gatesdrovme2it on 2012-02-05
Same problem as the OP- the authorization is always coming up for my wireless.  There are many of these threads around but no answers that have worked for me.

---

### Post by gatesdrovme2it on 2012-02-06
bump

---

### Post by gatesdrovme2it on 2012-02-07
hook a brother up!!!!  no ideas?

---

### Post by donwr on 2012-02-19
I have resolved the same problem very simply.
Click on Applications/System Tools/System Settings.
In the Hardware collection of icons, click on Network, then Wireless.
In the lower right hand corner of the Wireless Connected window (I earlier connected) click on Configure…
I have Connect Automatically checked (near the top), and Available to all users checked (near the bottom.
Click on the Wireless Security tab.
In my case for Security I have: WPA & WPA2 Personal
Fill in the Password.
Click Save.
When I restarted the system all went automatically.

---

### Post by bonjovi123 on 2012-08-11
I have to restart the hard switch couple of time for the wireless to connect. My wireless seems to work fine with certain network but not the one in my house. Im going with wired for a temp solution for now

---

### Post by ManiacMagee on 2012-09-28
Hi, I know this is an old thread, but I just had the same problem on a new install of Ubuntu 12.04.  To fix the issue, I went to the IPv6 settings for the network in question, and selected ignore under the "Method" drop-down menu.

---

### Post by NinjaTurtlez on 2012-11-09
I can't use wireless networks 90% of the time.
I have tried everything on this thread but it still doesn't work.
This type of bugs drives people away from Linux.

Check how many "Authentication required for wireless network" popups I have on my screen:

[[IMG]http://i.imgur.com/3egL8l.png[/IMG]](http://imgur.com/3egL8)

---

### Post by odinbaal on 2013-03-12
Thanks, ManiacMagee, that did it. :)

I've been plagued by this bug for ages. Surely this should be better documented?

Cheers!

---

