---
title: "wpa_supplicant and ifupdown not communicating?"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by vondo on 2006-06-26
The situation: I roam between three regular networks. Two have hidden SSIDs one is open. None use WEP or any security. I would also like to be able to have an "any" entry for picking up wireless at hotels, cafes, etc.

The problem is that ifup will only connect to the first SSID in my list because it seems that it doesn't wait for or know if wpa_supplicant has associtated with an AP. supplicant also spends quite a while (15 seconds?) trying to connect to each SSID. I shouldn't take that long, I would think.

So, if I bring up my network, I get a wpa_supplicant that just cycles through various SSIDs and doesn't stop cycling even if it associates and I get an ifup for which DHCP fails.  All this changes if I put the current SSID as the first entry in wpa_supplicant.conf, but that kind of defeats the purpose of using wpa_supplicant in the first place. I'll attach my interfaces and wpa_supplicant configurations.

Any ideas?

```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2 # Needed for hidden SSID
fast_reauth=1

network={
 ssid="vummiv" # Hidden 
 key_mgmt=NONE
 priority=3
}

network={
 ssid="vondo" # Hidden
 key_mgmt=NONE
 priority=2
}

network={
  ssid="tsunami" # Open
  key_mgmt=NONE
  priority=1
}

```

and

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
     wpa-conf /etc/wpa_supplicant.conf

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by leo_m on 2006-06-26
1.  If none of the links use any security, then why do you need wpa_supplicant?  Just take that line specifying wpa-conf out of your /etc/network/interfaces and you should be able to do away with wpa based authentication, since you do not need it.

2.  Use kde-wifi (kwifimanager) or ubuntu wifi-radar to have a nice GUI which tells you about available networks and then you can choose which one to associate with (I have not used these personally though, so do post a note if you can get it somewhere - kwifimanager was installed on Fedora that I had before switching to ubuntu)

If you like to write scripts and insist on using wpa_supplicant, e.g., to deal with hidden SSIDs or any future SSIDs which could contain WPA or WEP etc. based authentication, then have a look at the documentation inside /usr/share/doc/wpasupplicant/, also see the examples folder there which has an example roaming-daemon script. You could hack that script to first scan for the wireless networks available and outputting the results appropriately into a configuration file, then making the daemon use that file as the configuration file.

---

### Post by leo_m on 2006-06-26
I am installling kwifimanager and wifi-radar, will update if I find something interesting.

[update] done installation using Synaptic - I think wifi-radar will be more useful to you.  kwifimanager did not search for any networks since I have a *managed* or *infrastructure* type configuration.  However, wifi-radar still scanned for other APs present and had an option to connect to any of them, though I did not attempt that for obvious reasons.

---

### Post by vondo on 2006-06-26
[QUOTE=leo_m]1.  If none of the links use any security, then why do you need wpa_supplicant?  Just take that line specifying wpa-conf out of your /etc/network/interfaces and you should be able to do away with wpa based authentication, since you do not need it.

2.  Use kde-wifi to have a nice GUI which tells you about available networks and then you can choose which one to associate with (I have not used it personally though, so do post a note if you can get it somewhere - it was installed on Fedora that I had before switching to ubuntu)[/QUOTE]

1a. I have had occassion to connect to WEP networks as well.

2a. I don't want to have to select a particular network each time by running a GUI.

2b. KDE Wifi does not deal with hidden SSIDs well. It does not keep a list of what ones I've used, let alone what their priorities are. Even worse, my home network (which is hidden) is neglected in favor of my neighbors network which is not. This is not good.

2c. I want the wireless network up at boot (e.g. for ntp) not 30 seconds after I log in.

Frankly, I want it to work as well as Windows does for this situtation. Sadly, I have not found a linux solution that is even close.

---

### Post by leo_m on 2006-06-26
[QUOTE=vondo]1a. I have had occassion to connect to WEP networks as well.

2a. I don't want to have to select a particular network each time by running a GUI.

2b. KDE Wifi does not deal with hidden SSIDs well. It does not keep a list of what ones I've used, let alone what their priorities are. Even worse, my home network (which is hidden) is neglected in favor of my neighbors network which is not. This is not good.

2c. I want the wireless network up at boot (e.g. for ntp) not 30 seconds after I log in.

Frankly, I want it to work as well as Windows does for this situtation. Sadly, I have not found a linux solution that is even close.[/QUOTE]

1a. Even in Windows, you have to provide the WEP key for a newly discovered network - in Ubuntu, you provide that in the configuration file and then restart the roaming daemon - the roaming daemon is a script which would bring your wi-fi based on what you have in the configuration.  Both Windows and Linux assume that for secure networks, you have entered configuration somewhere.  In both, for unsecured networks, you can easily choose any available through GUI.

2a. Example, I have entered a particular network in my configuration for wpa_supplicant and it is up when I boot in Ubuntu - at boot time, without any further action on my part; and it is up faster than it is in Windows.  Despite having entered a network in the configuration and automatically logging on to that network, if I want to switch networks later, I can do that using the GUI.  If you have two different networks (in your case, 3, which I presume are all at different locations), then if you enter configuration for all of these in the configuration file, Ubuntu will automatically select the best one for you out of these at boot time.  If you need a network in a hotel temporarily for example, you can scan for networks using the GUI and select one then.

2b.  Can be overcome by putting configuration for your preferred networks in the config file and not use kdwifimanager at boot time.

2c.  Has been addressed in 2a above - if you configure all 3 networks in your configuration file, you will get wifi up at boot time, I get my wifi up at boot time.

Now, the core of the problem - in Windows, perhaps it is possible to mention your preferred network and if none of the preferred networks is available, then auto tune-in to the first one available (of course, such auto tune-in is possible for unsecured APs only, because for others it won't authenticate successfully since you never came across those networks before; well, perhaps.)

In Linux, I do not know if it is available through any tool currently. But you have a reasonable solution in that at boot time you are guaranteed to get one of the 3 you have configured in your config file.  Now I have not personally checked what wpa_supplicant will do if it cannot find any of those configured in the config file; but if the default behaviour then is to attach to any available, you are at par with Windows.  If not, it may require some work before it is possible - some cron script to scan network periodically if interface is not attached to any AP.

Sorry, at this point, am of no further help...

---

### Post by vondo on 2006-06-26
[QUOTE=leo_m]1a. Even in Windows, you have to provide the WEP key for a newly discovered network[/QUOTE]

Of course.

> 
2a. Example, I have entered a particular network in my configuration for wpa_supplicant and it is up when I boot in Ubuntu - at boot time, without any further action on my part; and it is up faster than it is in Windows.  Despite having entered a network in the configuration and automatically logging on to that network, if I want to switch networks later, I can do that using the GUI.  If you have two different networks (in your case, 3, which I presume are all at different locations), then if you enter configuration for all of these in the configuration file, Ubuntu will automatically select the best one for you out of these at boot time.  If you need a network in a hotel temporarily for example, you can scan for networks using the GUI and select one then.

2b.  Can be overcome by putting configuration for your preferred networks in the config file and not use kdwifimanager at boot time.


Ok, but this is what doesn't work for me, which is why I asked for help. I want ubuntu to select my network for me based on what SSIDs it can find, even if it has to try them because they are hidden. The wpa_supplicant and other file I provided will only give a functional connection if the SSID I am connecting to is listed FIRST.

Eric

---

### Post by leo_m on 2006-06-26
[QUOTE=vondo]... if I bring up my network, I get a wpa_supplicant that just cycles through various SSIDs and doesn't stop cycling even if it associates ...[/QUOTE]

This seems to be the cause of the problem - that wpa_supplicant keeps on cycling through SSIDs even if it has associated.

When I had not got my wpa_supplicant configuration quite right or was denied association to my AP (because I was using wrong authentication key), then due to that failed authentication, wpa_supplicant would get associated temporarily and then disconnect ... thus continuing to cycle through APs, none of which it found suitable because none was mentioned in my configuration file...

So, the solution would be, IMHO:

a) seeing why it discards a legitimate connection after association - look at messages spewed out by wpa_supplicant carefully, mostly it is due to some misconfiguration somewhere - I would recommend to try to attach to the *legitimate* but currently failing AP-connection in ad-hoc mode for debugging.
b) it would perhaps honour only those networks which are found in the configuration file: so there must be some script which scans for available networks and then creates a config file for wpa_supplicant, but should be called at boot time (and then periodically)...I have not checked but there could be some such tool out there already.

---

### Post by leo_m on 2006-06-26
[QUOTE=vondo]...Ok, but this is what doesn't work for me, which is why I asked for help. I want ubuntu to select my network for me based on what SSIDs it can find, even if it has to try them because they are hidden...[/QUOTE]

If we make the assumption that it is okay with you to use the GUI if you cannot find any one of the 3 networks, then I think you should _not scan at boot time and put your configuration for those 3 networks in managed mode_.  Thus, wpa_supplicant will not scan any at boot time and simply associate you with one of those 3 networks.

If you are at a location other than your 3 main networks, then probably you can use the GUI till someone writes a proper cron script for you.

From the top of example configuration file:```


##### Example wpa_supplicant configuration file ###############################
#
...
...
...
# Whether to allow wpa_supplicant to update (overwrite) configuration
#
# This option can be used to allow wpa_supplicant to overwrite configuration
# file whenever configuration is changed (e.g., new network block is added with
# wpa_cli or wpa_gui, or a password is changed). This is required for
# wpa_cli/wpa_gui to be able to store the configuration changes permanently.
# Please note that overwriting configuration file will remove the comments from
# it.
#update_config=1
```

oh, but it still means someone must write something which scans for new networks and adds/removes network blocks periodically to/from this file...

From wpa_cli README file:

```
Using wpa_cli to run external program on connect/disconnect
-----------------------------------------------------------

wpa_cli can used to run external programs whenever wpa_supplicant
connects or disconnects from a network. This can be used, e.g., to
update network configuration and/or trigget DHCP client to update IP
addresses, etc.

One wpa_cli process in "action" mode needs to be started for each
interface. For example, the following command starts wpa_cli for the
default ingterface (-i can be used to select the interface in case of
more than one interface being used at the same time):

wpa_cli -a/sbin/wpa_action.sh -B

The action file (-a option, /sbin/wpa_action.sh in this example) will
be executed whenever wpa_supplicant completes authentication (connect
event) or detects disconnection). The action script will be called
with two command line arguments: interface name and event (CONNECTED
or DISCONNECTED). If the action script needs to get more information
about the current network, it can use 'wpa_cli status' to query
wpa_supplicant for more information.

Following example can be used as a simple template for an action
script:

#!/bin/sh

IFNAME=$1
CMD=$2

if [ "$CMD" == "CONNECTED" ]; then
    SSID=`wpa_cli -i$IFNAME status | grep ^ssid= | cut -f2- -d=`
    # configure network, signal DHCP client, etc.
fi

if [ "$CMD" == "DISCONNECTED" ]; then
    # remove network configuration, if needed
fi

```

So, there need not be a cron script, instead what you need is an action script (modification in above template script) to update network blocks to the configuration file and then asking wpa_supplicant to reconfigure (after running a fresh scan, soon after a disconnection).  And then wpa_cli can be run in the background at boot time after wpa_supplicant is up by modifying scripts which bring wpa_supplicant into action.

So, now the main work is to create a proper action file, I suspect there is something out there which inserts new network blocks into the configuration file...best of luck with your search or authoring... :-)

---

### Post by vondo on 2006-06-28
Ok, lets forget out getting it to roam on networks I haven't seen before. And lets also assume that wpa_supplicant locks onto networks listed in my configuration file since I haven't seen it bypassing recently.

I still have two problems:

1) Ubuntu starts DHCP before wpa_supplicant has locked onto a network
2) wpa_supplicant spends so long (60 seconds) trying to scan each SSID that DHCP gives up before wpa_supplicant gets to the third network.

I cannot figure out a way to alter either of these problems. wpa_supplicant should not take more than a few seconds to figure out if an SSID is available, even if hidden. Instead it trys for a minute.

---

### Post by awaldram on 2006-06-28
Wifi radar is what your looking for.

my machine boots connected to the last network ascociated if thats not available it goes through the list (in the gui) till it finds one.

It starts from init.d so is up at boot.

and also a quick wifi-radar -d in my resume script ensures when resuming from hibernation the network is up even when the machine has changed location while asleep.

IMHO 
networkmanager nice eye candy bugger all use.(in dapper release)

networkmanager/wpa-supplicant were so badly broken 2 weeks prior to release that it is inusable.

---

### Post by vondo on 2006-06-28
[QUOTE=awaldram]Wifi radar is what your looking for.
[/QUOTE]

Thanks, I will check it out. Should I remove the wpa_supplicant packages?

---

### Post by awaldram on 2006-06-28
No wifi-radar will use wpa-supplicant if you set up a wpa connection
which is quite handy as that appears to be the only time the supplicant works

good luck

---

### Post by vondo on 2006-06-28
[QUOTE=awaldram]No wifi-radar will use wpa-supplicant if you set up a wpa connection
which is quite handy as that appears to be the only time the supplicant works

good luck[/QUOTE]

Ok, thanks. At the moment I am on one of the open networks that broadcasts SSID, so it works, of course. I will try in a couple of days on a hidden network.

Eric

---

### Post by awaldram on 2006-06-28
I can see a hidden network here (its marked as hidden) in the wifi-radar gui.

I can't connect to it as its not mine and wpa enabled , but I can see it and tell what encruption it uses

---

### Post by vondo on 2006-06-28
[QUOTE=awaldram]I can see a hidden network here (its marked as hidden) in the wifi-radar gui.

I can't connect to it as its not mine and wpa enabled , but I can see it and tell what encruption it uses[/QUOTE]

Ok, the problem I've always had with KDEWifi (or one of those) is that it would show hidden, you could tell it what the SSID was, but then it would never save that name and try it again later (like Windows). Instead, it would completely forget again the next time.

Eric

---

### Post by vondo on 2006-06-30
Well, wifi-radar is an improvement from wpa_gui in that it will do the ifup automatically and an improvement from the KDE tools in that it will save my SSID name, but it is not doing what I want.

It is not checking to see if a listed network is available if it is hidden on boot-up or otherwise. I still have to fire up the GUI and select the name of my hidden network. I want it to check automatically for a hidden SSID and move on down the list if it doesn't find it.

The readme in /usr/share/doc and the man pages are next to worthless when describing what the options are, they just give some examples and not an explanation of what the options are and what they do.

---

### Post by awaldram on 2006-06-30
Try running 'wifi-radar -d' this should connect to the first available network.

I have this in my resume script so that when my pc resume it attaches to the first avalable netork if in range, works well for me

---

### Post by vondo on 2006-06-30
[QUOTE=awaldram]Try running 'wifi-radar -d' this should connect to the first available network.

I have this in my resume script so that when my pc resume it attaches to the first avalable netork if in range, works well for me[/QUOTE]

That doesn't find hidden networks. I've tried running it with -d, it just keeps searching (not for the hidden network) until it times out. Care to post your config file?

---

### Post by awaldram on 2006-06-30
scan_timeout = 5
auto_profile_order = Waldram,blue,Pegasus,<hidden>
speak_up = False
ifup_required = False
interface = eth2
commit_required = False


[blue]
prescript =
use_wpa = no
postscript =
mode = auto
key =
use_dhcp = yes
security =
channel = auto

[Pegasus]
prescript =
use_wpa = yes
postscript =
mode = Managed
key =
use_dhcp = yes
security = open
wpa_driver = wext
channel = auto

[<hidden>]
prescript =
use_wpa = no
postscript =
mode =
key =
use_dhcp = yes
security =
channel =

[Waldram]
prescript =
use_wpa = no
postscript =
mode = auto
key = xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
use_dhcp = yes
security = open
wpa_driver = wext
channel = auto


I added the hidden one even though it wont work just so you can see how it should look.

These entries should be added as you set the profile up in the gui.

I've had to remove some as the networks as they are private and I cant publish the ssid's

the auto-profile order defines which order it searches for networks and which is preferential.

As in my case both Waldram and Pegasus are available at home but Waldram is the prefered  on with Pegasus the fail over

scan timeout defines how long to search for each network.

---

### Post by vondo on 2006-06-30
And are you saying that if you replace <hidden> with the real SSID for that network that it will connect *automatically* with no intervention? 

Because your format is exactly what I have and it will not connect. 


I turned on debugging in wifi-radar and it says:

Got current SSID  False
. Got current IP False

several time and then exits with "No preferred network found"

---

### Post by awaldram on 2006-07-01
That I'm not sure about as I dont have access to the netowork with the hidden ssid

---

### Post by awaldram on 2006-07-01
Just a quick thought 

what about leave it as hidden set up as wpa yes

then use a stanza in wpa_supplicant.conf to ascociate to the ap

Don't know if that will work for you as here with prim54,hostap and ipw2200 wpa_supplicant only work for wpa enrypted networks.

but you can see with the wpa_gui then set wifi-radar to call the stanza

---

### Post by leo_m on 2006-07-01
someone posted this too: [http://ubuntuforums.org/showthread.php?t=125150](http://ubuntuforums.org/showthread.php?t=125150) and I could see a HOWTO in this wireless-support area as well...[http://ubuntuforums.org/showthread.php?t=195259](http://ubuntuforums.org/showthread.php?t=195259)

---

