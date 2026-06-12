---
title: "Wifi Hotspt in Ubuntu 11.10"
date: 2012-03-09
forum: Networking &amp; Wireless
---

### Post by shuvabrata on 2012-03-09
I am using Ubuntu 11.10 along with Windows 7. I use a mobile broadband to connect to Internet. I have couple of Android phones which need Wi Fi access as well. In windows, i use Connectify. 

But in ubuntu, when i create a wireless connection as hotspot from Network, any other device fail to recognize that hotspot. Please help with detailed instructions.

regards,
Shuvabrata

---

### Post by alenis on 2012-03-10
Th problem might be that Android phones only connect to "infrastructure", not "ad hoc", networks. So I read somewhere, sorry that I can't be more specific.

---

### Post by mauleshjani on 2012-03-17
[SIZE=4]hi to all ...[/SIZE]
[SIZE=4]here i explain the method very simply... if u ll succeed do enjoy .....
[/SIZE][SIZE=3]hi i tried the method and it’s ok 100%
i again give the right tutorial …though the author is right always..
follow this…..====>
Just run this in the terminal:[/SIZE]
 [SIZE=3]sudo apt-get install hostapd[/SIZE]
 [SIZE=3]u ll get install hostapd (though u can’t see in DASH HOME)[/SIZE]
 [SIZE=3]OK NOW..[/SIZE]
 [SIZE=3]Then, open a text editor program, for example gedit. Copy the following into it.   [/SIZE]
 [SIZE=3]that means open — gedit —from DASH HOME[/SIZE]
 [SIZE=3]TYPE THE SAME WITH SOME CHANGES….[/SIZE]
 =======================================

[SIZE=3]interface=wlan0
driver=nl80211
ssid=
channel=1
hw_mode=g
auth_algs=1
wpa=3
wpa_passphrase=
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP
=======================================[/SIZE]
[SIZE=3]KEEP IN MIND THAT IN ABOVE LINES…..
ssid=   (is your network provider, e.g. mine is reliance EVDO)
SO I MODIFY ABOVE LINE AS THIS….[/SIZE]
 [SIZE=3]ssid=reliance EVDO[/SIZE]
 [SIZE=3]NOW
wpa_passphrase=  (is your desired password, e.g. mine is maulesh)
SO I MODIFY ABOVE LINE AS THIS….[/SIZE]
 [SIZE=3]wpa_passphrase=maulesh[/SIZE]
 [SIZE=3]OK NOW DO THIS …AND SAVE FILE GENERATED IN gedit…   [/SIZE]
 [SIZE=3]AS NAME  —– hostapd.conf    (IN YOUR HOME DIRECTORY)[/SIZE]
 [SIZE=3]OK NOW U FINISHED ONE PHASE TO MAKE YOUR UBUNUTU MACHINE VIRTUAL ROUTER….[/SIZE]
[SIZE=3]
[/SIZE]
 [SIZE=3]THE SECOND PHASE IS MORE IMPORTANT … (IF U FOLLOW OR UNDERSTAND ME CORRECTLY… THEN U WIN)[/SIZE]
[SIZE=3]
[/SIZE]
 [SIZE=3]NOW OPEN — network — from DASH HOME
GO TO OR OPEN — wireless —-
(see if wireless is ON or not …if OFF then ON it…)[/SIZE]
[SIZE=3]
[/SIZE]
 [SIZE=3]NOW PUT YOUR MOUSE CURSER TO THE RIGHT CORNER OF THE SCREEN AND CLICK … U SEE MANY NETWORKS THERE…[/SIZE]
 [SIZE=3]CLICK[/SIZE]
[SIZE=3]— create new wireless network —[/SIZE] [SIZE=3]U LL SEE A NEW WINDOW  AS THIS (I CAN’T DRAW SO SEE AS BELOW)[/SIZE]
 [SIZE=2]NEW WIRELESS NETWORK
CONNECTION                   (NEW)
NETWORK NAME              (BLANK)
WIRELESS SECURITY      (WEP 128-BIT PASSPHRASE)
KEY                                    (BLANK)[/SIZE]
 [SIZE=2](CANCEL)                                                   (CREATE)  [/SIZE]
 [SIZE=3]NOW FOLLOW ME>>>>[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=2]CONNECTION        (NEW)[/SIZE]
 [SIZE=2]NETWORK NAME   (your network name -as in hostapd.conf) ((for me reliance EVDO))[/SIZE]
 [SIZE=2]WIRELESS SECURITY  (WPA & WPA2 PERSONAL)  ((only select this to protect ur connection))[/SIZE]
 [SIZE=2]KEY  (your desired password -as in hostapd.conf) ((for me maulesh))[/SIZE]
 [SIZE=3]NOW CLICK                                (CREATE)[/SIZE]
 [SIZE=3]OK OK WAIT… JUST FOR SECONDS….[/SIZE]
 [SIZE=3]AGAIN PUT YOUR MOUSE CURSER TO THE RIGHT CORNER OF THE SCREEN AND CLICK … U SEE MANY NETWORKS THERE…[/SIZE]
 [SIZE=3]CLICK[/SIZE]

[SIZE=3]— connect to hidden wireless network —[/SIZE] [SIZE=3]U LL SEE A NEW WINDOW  AS THIS (I CAN’T DRAW SO SEE AS BELOW)[/SIZE]
 [SIZE=2]CONNECTION                    (NEW)
NETWORK NAME              (BLANK)
WIRELESS SECURITY      (BLANK)[/SIZE]
 [SIZE=2](CANCEL)                                                   (CREATE) [/SIZE]
 [SIZE=2]NOW CLICK ON CONNECTION … U LL DEFINITELY SEE YOUR CONFIGURED WIRELESS NETWORK (for me — reliance EVDO– )[/SIZE]
 [SIZE=2]OK NOW SELECT UR CONFIGURED NETWORK AND CLICK[/SIZE]
 [SIZE=2](CONNECT)[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]SO U VE NOW COMPLETED THE SECOND AND MOST IMPORTANT PHASE)[/SIZE]
[SIZE=3]
[/SIZE]
 [SIZE=3]JUST A FEW MINUTES TO OBSERVE OR CHECK WE R RIGHT/WRONG SO ..[/SIZE]
[SIZE=3]
[/SIZE]
 [SIZE=3]GO TO — terminal — from DASH HOME [/SIZE]
 [SIZE=3]GIVE THIS COMMAND ….  (don’t close this terminal until u r using network on other machine)[/SIZE]
[SIZE=3]
[/SIZE]
 [SIZE=3]sudo hostapd hostapd.conf[/SIZE]
[SIZE=3]
[/SIZE]
 [SIZE=3]AND NOW THE TERMINAL DANCE… N WE DANCE TOGETHER …
CHECK UR WIFI — in tablet or pc….
U LL NOTICE THE CONFIGURED NETWORK OPEN FOR U TO SERVE U BETTER ALWAYS…..
BYE… THANKS FOR FOLLOW ME….
my email is —- [EMAIL="elc12thsep00@yahoo.co.in"]elc12thsep00@yahoo.co.in[/EMAIL][/SIZE]
 [SIZE=3]and of course very very fond of LINUX UBUNTU …. and its USERS…..[/SIZE]
 [SIZE=3]THX…T.C….BYE….[/SIZE]

[SIZE=4]
[/SIZE]

---

### Post by vangop on 2012-06-26
Thanks a lot man, this seems to work after all the efforts I had earlier. The important part was setting a wireless connection in NM.

---

### Post by Sleepy-zz-John on 2012-10-08
Thanks for this article.  It's the best I've found so far.   but I'm still not able to pass any traffic through the new wifi link I've set up.  

I can see the wifi SSID I've created on my laptop appearing as a signal on both my symbian phone and my android.  They both prompt me for my network key which I've given them,  and then they try to obtain an IP address,  but this seems to be where they're failing.    No successful login

Meanwhile I'm seeing the following regularly repeated in Terminal:

```
wlan0: STA b8:d9:ce:f6:14:76 IEEE 802.11: authenticated
wlan0: STA b8:d9:ce:f6:14:76 IEEE 802.11: associated (aid 1)
AP-STA-CONNECTED b8:d9:ce:f6:14:76
wlan0: STA b8:d9:ce:f6:14:76 RADIUS: starting accounting session 50725710-0000001E
wlan0: STA b8:d9:ce:f6:14:76 WPA: pairwise key handshake completed (RSN)
AP-STA-DISCONNECTED b8:d9:ce:f6:14:76
wlan0: STA b8:d9:ce:f6:14:76 IEEE 802.11: disassociated
wlan0: STA b8:d9:ce:f6:14:76 IEEE 802.11: deauthenticated due to inactivity

```

On a previous attempt before I tried with hostapd, I did manage to create an ad hoc signal acceptable to my symbian phone using the simple basic Hotspot facility,  and using that I was able to successfully make a VOIP internet call on that phone,   but that ad hoc signal didn't show up at all on my android. 

For some reason this hostapd setup doesn't appear to be supporting DHCP when I've configured for "infrastructure"

---

