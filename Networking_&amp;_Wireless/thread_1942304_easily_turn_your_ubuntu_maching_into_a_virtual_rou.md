---
title: "easily turn your ubuntu maching into a virtual router"
date: 2012-03-17
forum: Networking &amp; Wireless
---

### Post by mauleshjani on 2012-03-17
[SIZE=2]hi i tried the method and it's ok 100%[/SIZE]
 [SIZE=2]i again give the right tutorial ...though the author is right always..[/SIZE]
 [SIZE=2]follow this.....====>[/SIZE]
 [SIZE=2]Just run this in the terminal:[/SIZE]
 [SIZE=2]
[/SIZE] 
 ```
sudo apt-get install hostapd
``` [SIZE=2]
[/SIZE] 
 [SIZE=2]u ll get install hostapd (though u can't see in DASH HOME)[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]OK NOW..[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]Then, open a text editor program, for example gedit. Copy the following into it.    [/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]that means open --- [/SIZE]_**gedit**_[SIZE=2] ---from _DASH HOME_[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]TYPE THE SAME WITH SOME CHANGES....[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]=======================================[/SIZE]
 ```
interface=wlan0
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
``` [SIZE=2]=======================================[/SIZE]
    
 [SIZE=2]KEEP IN MIND THAT IN ABOVE LINES.....[/SIZE]

 ```
ssid=   (is your network provider, e.g. mine is reliance EVDO)
``` [SIZE=2]SO I MODIFY ABOVE LINE AS THIS....[/SIZE]

 ```
ssid=reliance EVDO
``` [SIZE=2]
[/SIZE] 
 [SIZE=2]NOW[/SIZE]
 ```
wpa_passphrase=  (is your desired password, e.g. mine is maulesh)
``` [SIZE=2]SO I MODIFY ABOVE LINE AS THIS....[/SIZE]
 
 ```
wpa_passphrase=maulesh
``` [SIZE=2]
[/SIZE] 
 [SIZE=2]OK NOW DO THIS ...AND SAVE FILE GENERATED IN **_gedit.._**.    [/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]AS NAME  ----- **_hostapd.conf_**    (IN YOUR HOME DIRECTORY)[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]OK NOW U FINISHED ONE PHASE TO MAKE YOUR UBUNUTU MACHINE VIRTUAL ROUTER....[/SIZE]
   
 [SIZE=2]THE SECOND PHASE IS MORE IMPORTANT ... (IF U FOLLOW OR UNDERSTAND ME CORRECTLY... THEN U WIN)[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]NOW OPEN --- _**network**_ --- from _DASH HOME_[/SIZE]
 [SIZE=2]GO TO OR OPEN --- **_wireless_** ----[/SIZE]
 [SIZE=2](**see if wireless is ON or not ...if OFF then ON it...**)[/SIZE]
   
 [SIZE=2]NOW PUT YOUR MOUSE CURSER TO THE RIGHT CORNER OF THE SCREEN AND CLICK ... U SEE MANY NETWORKS THERE...[/SIZE]
   
 [SIZE=2]CLICK  [/SIZE]
 [SIZE=2]--- _**create new wireless network **_---[/SIZE]
 [SIZE=2]
[/SIZE] 
 _[SIZE=2]U LL SEE A NEW WINDOW  AS THIS (I CAN'T DRAW SO SEE AS BELOW)[/SIZE]_
 [SIZE=2]
[/SIZE] 
 [SIZE=2]
[/SIZE] 
 ```
NEW WIRELESS NETWORK
 CONNECTION                   (NEW)
 NETWORK NAME              (BLANK)
 WIRELESS SECURITY      (WEP 128-BIT PASSPHRASE)
 KEY                                    (BLANK)
   
 (CANCEL)                                                   (CREATE)   
``` [SIZE=2]NOW FOLLOW ME>>>>[/SIZE]
                                                                                   
 ```
CONNECTION        (NEW)
 
 
 NETWORK NAME   (your network name -as in hostapd.conf) ((for me reliance EVDO))
 
 
 WIRELESS SECURITY  (WPA & WPA2 PERSONAL)  ((only select this to protect ur connection))
 
 
 KEY  (your desired password -as in hostapd.conf) ((for me maulesh))
   
 
 
 NOW CLICK                                (CREATE)
 
```[SIZE=2]
[/SIZE] 
 [SIZE=2]
[/SIZE] 
 [SIZE=2]OK OK WAIT... JUST FOR SECONDS....[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]AGAIN PUT YOUR MOUSE CURSER TO THE RIGHT CORNER OF THE SCREEN AND CLICK ... U SEE MANY NETWORKS THERE...[/SIZE]
   
 [SIZE=2]CLICK  [/SIZE]
 [SIZE=2]--- **connect to hidden wireless network** ---[/SIZE]
 [SIZE=2]
[/SIZE] 
 _[SIZE=2]U LL SEE A NEW WINDOW  AS THIS (I CAN'T DRAW SO SEE AS BELOW)[/SIZE]_
 [SIZE=2]
[/SIZE] 
 ```
CONNECTION                    (NEW)
 NETWORK NAME              (BLANK)
 WIRELESS SECURITY      (BLANK)
 
 
   
 (CANCEL)                                                   (CREATE)  
``` [SIZE=2]
[/SIZE] 
 [SIZE=2]NOW CLICK ON CONNECTION ... U LL DEFINITELY SEE YOUR CONFIGURED WIRELESS NETWORK (for me -- reliance EVDO-- )[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]OK NOW SELECT UR CONFIGURED NETWORK AND CLICK[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2](CONNECT)[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]SO U VE NOW COMPLETED THE SECOND AND MOST IMPORTANT PHASE)[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]JUST A FEW MINUTES TO OBSERVE OR CHECK WE R RIGHT/WRONG SO ..[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]GO TO --- _**terminal**_ --- from _DASH HOME  _[/SIZE]
   
 [SIZE=2]GIVE THIS COMMAND .... (don't close this terminal until u r using network on other machine)[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]
[/SIZE] 
 ```
sudo hostapd hostapd.conf
``` [SIZE=2]
[/SIZE] 
 [SIZE=2]AND NOW THE TERMINAL DANCE... N WE DANCE TOGETHER ...[/SIZE]
 [SIZE=2]CHECK UR WIFI --- in tablet or pc....  [/SIZE]
 [SIZE=2]U LL NOTICE THE CONFIGURED NETWORK OPEN FOR U TO SERVE U BETTER ALWAYS.....[/SIZE]
 [SIZE=2]BYE... THANKS FOR FOLLOW ME....[/SIZE]
 
 [SIZE=2]
[/SIZE] 
 [SIZE=2]and of course very very fond of LINUX UBUNTU .... and its USERS.....[/SIZE]

---

### Post by praseodym on 2012-03-17
Hi, thanks for that. You may want to edit the posting and mark the terminal commands and the file inputs and click on the #-button in advanced mode for code-tags. It will make it easier to read ;-)

---

### Post by mauleshjani on 2012-03-17
> **praseodym said:**
> Hi, thanks for that. You may want to edit the posting and mark the terminal commands and the file inputs and click on the #-button in advanced mode for code-tags. It will make it easier to read ;-)


yes sir, 
as per your instruction  .. i have done .... 
thanks for giving me proper way to edit 
thx...

---

