---
title: "Karmic bluetooth problems"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by keithspg on 2010-03-28
This seems to be my last remaining problem. I struggled with BT doing nothing useful at all for a while. Recently, I added the gnome/bt repository ([http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) karmic main) and it updated the BT group of programs. After it updated, I could actually negotiate a pairing. Now, it is not actually consistent, but I can negotiate a pairing.

The Nokia I have paired has gone away and returned. When it came back, it connected and I was able to browse files, send a file via BT. So, it appears that the BT dongle is supported by the software and the latest code allows it to connect. Now, the iPhone is a different story. I can pair the iPhone, but not every time. Also, once paired according to BT mgr, it will not automatically connect. I was able to negotiate a PANU network once, but not since. In the iPhone on the BT page, it shows 'not connected' and just spins and spins on the iphone. If I remove this connection and try to negotiate again, I get nothing on the iPhone. Sometimes I can get the iPhone to show up and I get a 6 digit code, but nothing ever shows up on the phone. I mention this only b/c it should work and it does not. I am not bothered much by this as I can always cable connect it and that works for tethering. 

The big issue I have is with my BT serial connecton. I have never been able to connect to it. With the latest update of the BT bundle, I can see the serial port in BT manager, but I cannot use the '1234' code. I select 'use fixed code and the 1234, but it always tries to give it a 6 digit code and this will not allow a connect. May this be because the BT serial port is in 'master' mode? I have this BT serial (RN-41) paired with this BT dongle so that it will pair with this and only this MAC, but it still requires a '1234' code to be sent. 

Please help.

Keith

---

### Post by keithspg on 2010-03-29
In the case that someone is interested and reading this, The latest update is that I uninstalled "gnome-bluetooth" and installed "bluez-gnome". This GUI interface allows me to actually send the '1234' code and I was able to actually pair with my serial port that requires a '1234' code. It now shows up in the list of paired devices in the bluez-gnome dialog box (different dialog box than the gnome-bluetooth panel).

Now I need to set up the serial port and see how that works. Still unsure how to do that. In XP, it just shows up. It seems like I need to use rfcomm, but I will have to research this some more. Any help appreciated. 

Keith

---

### Post by keithspg on 2010-03-29
I have confirmed that the bluez gnome package works better for me and my BT dongle. I do not know why, but with the gnome-bluetooth, I cannot send the 1234 *and* it now connects to my iPhone in BT as a my internet tethering device. So, for now I am off gnome-bluetooth and now using bluez-gnome. I could care less as long as it works. Now, I still do not know how to connect to my serial port via BT. These are the commands I issued and the response.  

Notice when I scan with the hcitool, I see nothing but if I ask specifically about the MAC address of the BT serial device, 00:06:66:02:d3:95, I get stuff. I still do not know how to set up a rfcomm port. The confusing info on the web calls for programs which are not installed and do not suggest what should be installed via apt-get.

If anyone can help, please suggest something. 

```
>sudo hcitool info 00:06:66:02:d3:95
Requesting information ...
    BD Address:  00:06:66:02:d3:95
    Device Name: FireFly-D395
    LMP Version: 2.1 (0x4) LMP Subversion: 0x1333
    Manufacturer: Cambridge Silicon Radio (10)
    Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x59 0x83
        <3-slot packets> <5-slot packets> <encryption> <slot offset> 
        <timing accuracy> <role switch> <hold mode> <sniff mode> 
        <park state> <RSSI> <channel quality> <SCO link> <HV2 packets> 
        <HV3 packets> <u-law log> <A-law log> <CVSD> <paging scheme> 
        <power control> <transparent SCO> <broadcast encrypt> 
        <EDR ACL 2 Mbps> <EDR ACL 3 Mbps> <enhanced iscan> 
        <interlaced iscan> <interlaced pscan> <inquiry with RSSI> 
        <extended SCO> <EV4 packets> <EV5 packets> <AFH cap. slave> 
        <AFH class. slave> <3-slot EDR ACL> <5-slot EDR ACL> 
        <sniff subrating> <pause encryption> <AFH cap. master> 
        <AFH class. master> <EDR eSCO 2 Mbps> <EDR eSCO 3 Mbps> 
        <3-slot EDR eSCO> <extended inquiry> <simple pairing> 
        <encapsulated PDU> <non-flush flag> <LSTO> <inquiry TX power> 
        <extended features> 
>sudo hcitool con
Connections:
    > ACL 00:06:66:02:D3:95 handle 0 state 1 lm MASTER AUTH 
>sudo sdptool browse 00:06:66:02:d3:95
Browsing 00:06:66:02:D3:95 ...
>hcitool scan
Scanning ...
    00:1E:3D:1D:36:9E    n/a
>sudo rfcomm connect 00:06:66:02:d3:95
Can't find a config entry for rfcomm0
>sudo hidd --connect 00:06:66:02:d3:95
sudo: hidd: command not found
```

---

### Post by keithspg on 2010-03-30
Ok, further testing. I set up the /etc/bluetooth/rfcomm.conf file with what I think is close to correct:

```
rfcomm0 {
    # Automatically bind the device at startup
    bind yes;

    # Bluetooth address of the device
    device 00:06:66:02:D3:95;

    # RFCOMM channel for the connection
    channel    1;

    # Description of the connection
    comment "Firefly d395";
}
```This morning I was able to see it, though not in an "hcitool scan"

```
$ sudo hcitool info 00:06:66:02:d3:95
Requesting information ...
    BD Address:  00:06:66:02:d3:95
    Device Name: FireFly-D395
    LMP Version: 2.1 (0x4) LMP Subversion: 0x1333
    Manufacturer: Cambridge Silicon Radio (10)
    Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x59 0x83
        <3-slot packets> <5-slot packets> <encryption> <slot offset> 
        <timing accuracy> <role switch> <hold mode> <sniff mode> 
        <park state> <RSSI> <channel quality> <SCO link> <HV2 packets> 
        <HV3 packets> <u-law log> <A-law log> <CVSD> <paging scheme> 
        <power control> <transparent SCO> <broadcast encrypt> 
        <EDR ACL 2 Mbps> <EDR ACL 3 Mbps> <enhanced iscan> 
        <interlaced iscan> <interlaced pscan> <inquiry with RSSI> 
        <extended SCO> <EV4 packets> <EV5 packets> <AFH cap. slave> 
        <AFH class. slave> <3-slot EDR ACL> <5-slot EDR ACL> 
        <sniff subrating> <pause encryption> <AFH cap. master> 
        <AFH class. master> <EDR eSCO 2 Mbps> <EDR eSCO 3 Mbps> 
        <3-slot EDR eSCO> <extended inquiry> <simple pairing> 
        <encapsulated PDU> <non-flush flag> <LSTO> <inquiry TX power> 
        <extended features> 
```And I made a connection, though nothing showed up, yet. I may have the twrong channel. I'll try channel 2 tonight.

```
$ rfcomm connect 0
Connected /dev/rfcomm0 to 00:06:66:02:D3:95 on channel 1
Press CTRL-C for hangup
Disconnected
```

---

### Post by keithspg on 2010-03-30
So, I tried Blueman tonight instead of gnome-bluetooth or bluez-gnome. Am I the only one having troubles with this? Blueman seems more complete. It actually allowed a serial connection and set up /dev/rfcomm0 for me. This was further than I had gotten previously, but still no joy as the serial port I want is the second one and blueman did not detect it. Also, Blueman seems to have other issues. Upon boot, I get the 'failed to set bluetooth power' error and it wants to go 'grey' and not respond at times. In the log it is always timeout issues. This does not appear to be specific to me but I have not yet found a solution. The edit to main.conf seems to make no difference.

So, in summary, they are all not adequate for what I want to do. If you want to connect to a phone in either panu or obex mode, I recommend bluez-gnome. I do not recommend gnome-bluetooth as it is capable of only obex connections to phones. I do not recommend blueman, though I would like to as it is more complete and seems more capable if it would 1) detect all of the services on a device 2) not time out.

I am aware that these are front ends on other programs (bluez stack?), The problem I have is that I have no clue at all as to what programs those are. The blueman web page is not helpful neither is the gnome-bluetooth or bluez. I have not yet found a command line program that will show the serial port that appears in blueman or bluez any more than whayt I have posted above. hciconfig will only see it when I put in the mac address. Scanning shows nothing. Also, I do not know how to query the device so that I know what services are there. If I could, I may be able to figure out how to set up the comm port. 

If anyone can help or direct me as to what I am doing wrong, please post.

Frustrating

---

### Post by lillebj0rn on 2010-03-31
I'm having the same problem with my Acer One laptop and Nokia 6220classic.
First i tried manually editing rfcom0. No luck yet.

Currently trying with bluetooth assistant:
[http://blueman-project.org/](http://blueman-project.org/) 

It allows me to pair, browse files etc.
I cannot get DUN to work (dial up network i think)

Anyone have any suggestions?

---

### Post by keithspg on 2010-03-31
> **herry.james said:**
> Plug it in and search for drivers automatically recommended when prompt  to do so, it will download.
? I do not get this suggestion. gnome-bluetooth is installed as default. That was what was on there when I first plugged in the adapter and it only partially worked. It is my search to get all my bluetooth devices to work and it appears that bluetooth-gnome does not support all of them for varying reasons. I do not understand why this 'manager' was selected by canonical for the default package when it is missing many components and capabilities.

blueman is much more capable and communicative.

Keith

---

### Post by keithspg on 2010-04-02
Ok, I give up. I'll wait for a while and see if this gets any better after Lucid is released (doubtful). I have spend uncounted hours in the evening trying to get this thing to work and am 'done'. it is my opinion that the tools available are not adequate to the task I am putting them to. For most applications and uses, it appears to work fine, but with a serial port configured how I have it these tools are inadequate. The command line Bluez commands are poorly documented and have changed dramatically over the past year and a half and it does not seem that anyone really knows how to do what I am suggesting. If I could just get sdptool to show me teh services on this device, I could set up teh rfcomm.conf file to connect and bind, but I do not know which port it is. I have tried "1" and "2" to no avail.

As I said before, the gnome-bluetooth applet (which is standard, canonical-selected applet) is useful only for obex file transfer for whatever reason, has trouble pairing and finding a PANU connection and cannot pair with a fixed pin device at all. The Blueman applet appears to be the most complete and most robust. It is not perfect as it still gets timeouts and such, but it is much more complete than the other 2.

Keith

---

### Post by keithspg on 2010-05-17
Ok, since nobody here seemed to know and every web page I came across referred to using rfcomm connect, I assumed that was what I wanted. I finally found someone to help and he figured it out in a couple minutes. So here it is if you want to use a BT serial port in Ubuntu.

Set up your /etc/bluetooth/rfcomm.conf similar to this:
```
#
# RFCOMM configuration file.
#
rfcomm0 {
    # Automatically bind the device at startup
    bind no;

    # Bluetooth address of the device
    device 00:00:00:00:00:00;  # serial port mac address

    # RFCOMM channel for the connection
    channel    1;

    # Description of the connection
    comment "Example Bluetooth device";
}

```

Then what you want is to 'bind' this address. I added this to the end of my /etc/init.d/rc.local

```

/usr/bin/rfcomm bind 0
```

This will create the connection. When the BT device appears, it makes it a valid serial port. When it goes away, it just fails silently. Works every time for me.

KeithSPG

---

### Post by cocoa117 on 2010-06-12
Thanks for continue feedback on your findings, I just start to use bluetooth and Internet tethering with my Nokia 2730 classic. I am using Lucid, and it seems fully working with following procedure.

1. install blueman PPA package
sudo add-apt-repository ppa:blueman/ppa
sudo apt-get update
sudo apt-get install blueman

2. pairing your phone and ubuntu. This should be straight forward process on Lucid

3. preparing serial ports for bluetooth on Ubuntu (it basically using your method here)
* Set up your /etc/bluetooth/rfcomm.conf similar to this

rfcomm0 {
    # Automatically bind the device at startup
    bind no;

    # Bluetooth address of the device
    device 00:00:00:00:00:00;  # serial port mac address

    # RFCOMM channel for the connection
    channel    1;

    # Description of the connection
    comment "Example Bluetooth device";
}

* added this to the end of my /etc/init.d/rc.local
/usr/bin/rfcomm bind 0

P.S. I just find I can skip step 3, and still be able to make connection, anyone got any different results?

4. Now, right click on the phone, and select Serial Ports->Dialup Service. Your phone should show icon where the tethering is up

5. Click on the NetworkManager, and select the Mobile Broadband connection (depending on your network)

Then your laptop should be able to do Internet tethering over your bluetooth connection.

---

### Post by keithspg on 2010-06-12
Awesome! Now if the 'ghost devices' that I cannot remove would just go away in 10.04, I would be happy. 

In the attached screen grab, the 'firefly' is mine and I have paired it. the rest show up under Blueman or Gnome Bluetooth (useless in comparison to blueman, IMO). I cannot delete them. If I do manage to delete them (sometimes the interface allows it !?) they show back up after a reboot. BT works, but it is just annoying to have this.

Keith

---

