---
title: "Setting defaults for bluetooth PatriotBTSpeaker"
date: 2017-07-02
forum: Multimedia Software
---

### Post by navegantefox on 2017-07-02
Have to reset the bluetooth connection every time I turn the speaker on. There is no Autodetect function like there is in Windows.
Also need to set the sound settings manually every time and it doesn't always work.
Is there a way to make Ubuntu auto detect the speaker and load the correct sound settings?

---

### Post by mc4man on 2017-07-02
bluetooth in linux & ubuntu is overall terrible, ubuntu ignored many bugs for some time. (there are some pulseaudio fixes now, xenial-proposed & in 17.10
Here in 16.04 & 17.10 it works ok once connected, both can have issues connecting (pairing is fine), many times I have to remove & re-add the device, (bluetooth speaker) before it stays connected..

I've found 1 way to auto connect with proper output device but it seems fragile & ymmv would be a huge understatement. Also it doesn't appear to stay working if I boot to another Os & connect or auto-connect to the speaker. In that case usually have to again remove & re-add the device to get going.
In other words this could be useless to some, works ok here
..
Also note: this is just useful in the case_ where speaker is on & then one boots up computer_ which is the most likely case for me. (log in could also work


[COLOR="#FF0000"]Edit:[/COLOR]
As of recent in 16.04 I no longer need the startup script, only the /etc/pulse/default.pa edit.
With that now if already in a session & bluetooth speaker is then powered on it will pair & connect..

Only on 16.04 or up
Basically a script & a startup app.
 (- script here marked exec & in ~/.bin, startup .desktop is in ~/.config/autostart.

The XX:XX.. is replaced by actual device id, can be seen in bluetooth settings on the device or run just bluetoothctl in a terminal, should show up.

script.
(- the 2nd set is because here many times the device connects then disconnects within 7 sec, the 2nd set then  holds.
Sleep times are what works here, 12 secs on 2nd run makes sure if device is going to disconnect it  actually has disconnected, otherwise 2nd run has no affect either way.
```

#!/bin/bash
bluetoothctl 
sleep 10
echo "connect XX:XX:XX:XX:XX:XX" | bluetoothctl
sleep 12
echo "connect XX:XX:XX:XX:XX:XX" | bluetoothctl
exit
```

The startup .desktop
The Exec= is the name of the above script, here named auto1

```
[Desktop Entry]
Type=Application
Exec=auto1
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=auto1
X-GNOME-Autostart-Delay=5
Comment=Starts Bluetooth speaker
```

To get pulse audio to behave - 
```
sudo -H gedit /etc/pulse/default.pa
```
Add this under the .ifexists module-bluetooth-discover.so section, shown in screen
```
.ifexists module-switch-on-connect.so
load-module module-switch-on-connect
.endif
```

So here to set up 16.04, 
Put the script in ~/bin, marked exec
Create with gedit,  ~/.config/autostart/auto1.desktop
Edit default.pa
Open bluetooth settings, removed the speaker, then added it back, reconnected
Reboot
Here in unity it's then just watch the panel icon for the script activities,,, then try player, ect.

---

