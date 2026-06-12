---
title: "Bluetooth speakers not working correctly."
date: 2010-11-16
forum: Multimedia Software
---

### Post by dmcosta on 2010-11-16
Hello.

I have a Asus EeePc 1008HA and also a Sony SRS-BT100 bluetooth speakers.

When I pair them with ubuntu for the first time, every thing was ok. They paired and I could activate the audio sink service with success.
The problem is when I disconnect the audio sink (turn off netbook, or reboot) and then want to reconnect to the paired and trusted device. I can't...

I've tried to pair and connect via terminal, but the issue is the same only the 1st time....

If I want to use the speakers with Ubuntu again I have to remove the device pair it again and then I can connect...

Can some help me please?

I'm using: 

Ubuntu 10.10
bluez 4.69-0ubuntu2
blueman 1.21
pulseaudio 1:0.9.22

---

### Post by pricetech on 2010-11-16
Have you tried "bluetooth" ??  Mines just a bluetooth earbud, but I've had no trouble with it.  I do have to reconnect after a reboot, after I turn off the earbud, or after I walk beyond its range, but never had to remove and add it back.

My bluetooth is a TrendNet TBW 105 UB USB adapter paired with a disused Samsung bluetooth earbud.  The adapter is Broadcom based if that helps.

---

### Post by dmcosta on 2010-11-16
Hi pricetech.

Thanks for the reply.

Yes I've tried "bluetooth", and more of the same. It pairs and connects. Then I reboot and check. The speakers are paired and trusted, but on "bluetooth" I don't even have the option to "connect to audio sink"

I've tried to run this script and do it "manually" but the results are the same.

```

BT_BDADDR=00:1D:BA:33:2B:5A
echo "Selected bluetooth device: $BT_BDADDR"
 
echo "Writing new ~.asoundrc..."
cat >> ~/.asoundrc <<EOD
pcm.bt_audioraw {
        type bluetooth
        device $BT_BDADDR
        profile "auto"
}
pcm.bt_audio {
	type plug
        slave.pcm "bt_audioraw"
        hint {
            show on
            description "Bluetooth audio device"
        }
}
EOD
 
echo "Getting default adapter..."
_BT_ADAPTER=`dbus-send --system --print-reply --dest=org.bluez / \
    org.bluez.Manager.DefaultAdapter|awk '/object path/ {print $3}'`
BT_ADAPTER=${_BT_ADAPTER//\"/}
echo "$BT_ADAPTER"
 
echo "Removing any stale Bluetooth audio device:"
_OLD_BT_DEVICE=`dbus-send --system --print-reply --dest=org.bluez $BT_ADAPTER \
    org.bluez.Adapter.FindDevice string:$BT_BDADDR|awk '/object path/ {print $3}'`
OLD_BT_DEVICE=${_OLD_BT_DEVICE//\"/}
dbus-send --system --print-reply --dest=org.bluez $BT_ADAPTER \
    org.bluez.Adapter.RemoveDevice objpath:$OLD_BT_DEVICE
 
echo "Creating Bluetooth audio device:"
_BT_DEVICE=`dbus-send --system --print-reply --dest=org.bluez $BT_ADAPTER \
    org.bluez.Adapter.CreateDevice string:$BT_BDADDR|awk '/object path/ {print $3}'`
BT_DEVICE=${_BT_DEVICE//\"/}
echo "$BT_DEVICE"
 
echo "Connecting -- BlueZ applet will prompt for pin..."
dbus-send --system --print-reply --dest=org.bluez \
$BT_DEVICE org.bluez.AudioSink.Connect

```

Once again, if I've just paired the speakers it works, if already paired and disconnected (at least I think they're disconnected) it fails to reconnect.


Thanks.

---

### Post by dmcosta on 2010-11-17
Anyone? Please?

---

