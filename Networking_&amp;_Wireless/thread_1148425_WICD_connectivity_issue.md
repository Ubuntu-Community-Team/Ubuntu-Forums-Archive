---
title: "WICD connectivity issue"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by js71 on 2009-05-04
I did a clean install to 9.04 and was unable to use wireless at all with network manager so I installed WICD.  Now the problem, WICD doesn't see my hidden SSID and therefore won't connect.  The only way I can connect is to enable broadcasting of my SSID, connect to it, then disable the broadcasting again which is what I want.  I stay connected fine as long as I don't reboot, logoff, etc.  My questoin is, how can I configure WICD to always connect to my network without having to perform the above steps each time? 

I haven't installed Wifi-Radar yet, would that be an option? 

Any help is much appreciated.

Thanks

---

### Post by SuperSonic4 on 2009-05-04
What happens if you run ```
iwlist scan
```

There is a section about hidden ESSIDs on the Arch Wiki page for wicd (should work the same): [http://wiki.archlinux.org/index.php/Wicd#Hidden_Wireless_Networks_and_Autoconnection_HACK](http://wiki.archlinux.org/index.php/Wicd#Hidden_Wireless_Networks_and_Autoconnection_HACK)

---

### Post by papangul on 2009-05-04
On the top left corner besides he "network" tab there is a small arrow like pointer, on clicking it can you see the "hidden network" item ? Hope this works.
 
Hiding essid makes no sense from security point of view.

---

### Post by js71 on 2009-05-04
I see the arrow, typed the name of my network and it didn't add it to the list after a refresh.

---

### Post by papangul on 2009-05-04
You have to understand one thing. WICD or any NM has to make the network PSK(pre-shared key) using the essid and passphrase as input parameters. That's why the other day you were seeing the long string of literals in the NM when you entered your password.

open the terminal and type the following:

$wpa_passphrase <your network essid>  <your password>

So wicd has to know either the name of the network and the password, or the output of the above command beforehand, otherwise it will not be able to connect to your network when you hide the essid.

---

### Post by js71 on 2009-05-04
Thanks, I can't test this now as I'm not at home but this is the output of that command on a test pc here at work: 

wpa_passphrase test testtesttest
network={
    ssid="test"
    #psk="testtesttest"
    psk=b6df3a2ab8a19db1b646e4a852892d39fc4e73c13cb2ade0ad9d8887bb414ecd
}

So by running that command you mentioned I should be able to connect to my home wireless without issue according to what is seen above? I guess I'm just a little confused by the long alpha-numeric sting next to "psk=".  Will my key stay in the properties of my network in WICD after this command is ran?

-js

---

