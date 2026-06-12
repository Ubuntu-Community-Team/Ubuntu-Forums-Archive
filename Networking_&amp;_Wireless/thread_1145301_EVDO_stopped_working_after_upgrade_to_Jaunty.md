---
title: "EVDO stopped working after upgrade to Jaunty"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by kallahar on 2009-05-01
Hello, I just upgraded from Intrepid to Jaunty and my EVDO card stopped working.  I've searched all over but I haven't had any luck figuring out what the problem is.  It successfully gets an IP address, but then 15-30 seconds later it disconnects with a "pppd_timed_out(): Looks like pppd didn't initialize our dbus module" error in daemon.log

Any ideas?  Below is all the logs I think are relevant...  Let me know if I should get more info.  I also thought it might work to just replace all the networking config files with their defaults, but I'm not sure how to do that.

Kallahar



Sierra Wireless EVDO card from Sprint
Ubuntu Jaunty Jackalope, fully up to date as of 5/1/2009


/var/log/messages when inserting device:

May  1 11:13:16 dell1833 kernel: [67036.784108] usb 2-5: USB disconnect, address 12
May  1 11:13:18 dell1833 kernel: [67038.160047] usb 2-5: new full speed USB device using ohci_hcd and address 13
May  1 11:13:18 dell1833 kernel: [67038.373099] usb 2-5: configuration #1 chosen from 1 choice
May  1 11:13:18 dell1833 kernel: [67038.376024] sierra 2-5:1.0: Sierra USB modem converter detected
May  1 11:13:18 dell1833 kernel: [67038.379207] usb 2-5: Sierra USB modem converter now attached to ttyUSB0
May  1 11:13:18 dell1833 kernel: [67038.379275] usb 2-5: Sierra USB modem converter now attached to ttyUSB1
May  1 11:13:18 dell1833 kernel: [67038.379336] usb 2-5: Sierra USB modem converter now attached to ttyUSB2
May  1 11:13:18 dell1833 kernel: [67038.388918] scsi18 : SCSI emulation for USB Mass Storage devices
May  1 11:13:23 dell1833 kernel: [67043.462050] scsi 18:0:0:0: Direct-Access     Sierra   Wireless Storage 2.31 PQ: 0 ANSI: 2
May  1 11:13:23 dell1833 kernel: [67043.479179] sd 18:0:0:0: [sdf] Attached SCSI removable disk
May  1 11:13:23 dell1833 kernel: [67043.479308] sd 18:0:0:0: Attached scsi generic sg6 type 0





/var/log/messages when clicking connect from NetworkManager

May  1 11:08:10 dell1833 pppd[26384]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
May  1 11:08:10 dell1833 pppd[26384]: pppd 2.4.5 started by root, uid 0
May  1 11:08:10 dell1833 pppd[26384]: Using interface ppp0
May  1 11:08:10 dell1833 pppd[26384]: Connect: ppp0 <--> /dev/ttyUSB0
May  1 11:08:10 dell1833 pppd[26384]: local  IP address 72.62.188.178
May  1 11:08:10 dell1833 pppd[26384]: remote IP address 68.28.57.69
May  1 11:08:10 dell1833 pppd[26384]: primary   DNS address 68.28.58.92
May  1 11:08:10 dell1833 pppd[26384]: secondary DNS address 68.28.50.91

May  1 11:08:25 dell1833 pppd[26384]: Terminating on signal 15
May  1 11:08:25 dell1833 pppd[26384]: Connect time 0.3 minutes.
May  1 11:08:25 dell1833 pppd[26384]: Sent 0 bytes, received 0 bytes.
May  1 11:08:25 dell1833 pppd[26384]: Connection terminated.
May  1 11:08:25 dell1833 pppd[26384]: Exit.




/var/log/daemon.log

May  1 11:08:57 dell1833 NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Sprint EVDO' 
May  1 11:08:57 dell1833 NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
May  1 11:08:57 dell1833 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
May  1 11:08:57 dell1833 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
May  1 11:08:57 dell1833 NetworkManager: <debug> [1241201337.831643] nm_serial_device_open(): (ttyUSB0) opening device... 
May  1 11:08:57 dell1833 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
May  1 11:08:57 dell1833 NetworkManager: <info>  (ttyUSB0): powering up... 
May  1 11:08:58 dell1833 NetworkManager: <info>  Connected, Woo! 
May  1 11:08:58 dell1833 NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled... 
May  1 11:08:58 dell1833 NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting... 
May  1 11:08:58 dell1833 NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 
May  1 11:08:58 dell1833 NetworkManager: <info>  Starting pppd connection 
May  1 11:08:58 dell1833 NetworkManager: <debug> [1241201338.869209] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyUSB0 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/3 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so 
May  1 11:08:58 dell1833 NetworkManager: <debug> [1241201338.888634] nm_ppp_manager_start(): ppp started with pid 26435 
May  1 11:08:58 dell1833 NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete. 

May  1 11:09:13 dell1833 NetworkManager: <WARN>  pppd_timed_out(): Looks like pppd didn't initialize our dbus module 
May  1 11:09:13 dell1833 NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 9 
May  1 11:09:13 dell1833 NetworkManager: <debug> [1241201353.842302] nm_serial_device_close(): Closing device 'ttyUSB0' 
May  1 11:09:13 dell1833 NetworkManager: <info>  Marking connection 'Sprint EVDO' invalid. 
May  1 11:09:13 dell1833 NetworkManager: <info>  Activation (ttyUSB0) failed. 
May  1 11:09:13 dell1833 NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
May  1 11:09:13 dell1833 NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0). 
May  1 11:09:13 dell1833 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
May  1 11:09:13 dell1833 NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
May  1 11:09:13 dell1833 NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
May  1 11:09:15 dell1833 NetworkManager: <debug> [1241201355.836414] ensure_killed(): waiting for ppp pid 26435 to exit 
May  1 11:09:15 dell1833 NetworkManager: <debug> [1241201355.836747] ensure_killed(): ppp pid 26435 cleaned up 



/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
debug
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4

---

### Post by kallahar on 2009-05-01
Oh, and auth.log

May  1 13:13:08 dell1833 dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.39" (uid=1000 pid=10186 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.294" (uid=0 pid=2219 comm="/usr/sbin/pppd nodetach lock nodefaultroute ttyUSB"))
May  1 13:13:08 dell1833 dbus-daemon: Rejected send message, 7 matched rules; type="method_call", sender=":1.294" (uid=0 pid=2219 comm="/usr/sbin/pppd nodetach lock nodefaultroute ttyUSB") interface="org.freedesktop.NetworkManager.PPP" member="SetState" error name="(unset)" requested_reply=0 destination="org.freedesktop.NetworkManager" (uid=0 pid=25392 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))
May  1 13:13:08 dell1833 dbus-daemon: Rejected send message, 7 matched rules; type="method_call", sender=":1.294" (uid=0 pid=2219 comm="/usr/sbin/pppd nodetach lock nodefaultroute ttyUSB") interface="org.freedesktop.NetworkManager.PPP" member="SetState" error name="(unset)" requested_reply=0 destination="org.freedesktop.NetworkManager" (uid=0 pid=25392 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))
May  1 13:13:08 dell1833 dbus-daemon: Rejected send message, 7 matched rules; type="method_call", sender=":1.294" (uid=0 pid=2219 comm="/usr/sbin/pppd nodetach lock nodefaultroute ttyUSB") interface="org.freedesktop.NetworkManager.PPP" member="SetState" error name="(unset)" requested_reply=0 destination="org.freedesktop.NetworkManager" (uid=0 pid=25392 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))
May  1 13:13:08 dell1833 dbus-daemon: Rejected send message, 7 matched rules; type="method_call", sender=":1.294" (uid=0 pid=2219 comm="/usr/sbin/pppd nodetach lock nodefaultroute ttyUSB") interface="org.freedesktop.NetworkManager.PPP" member="SetState" error name="(unset)" requested_reply=0 destination="org.freedesktop.NetworkManager" (uid=0 pid=25392 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))
May  1 13:13:08 dell1833 dbus-daemon: Rejected send message, 7 matched rules; type="method_call", sender=":1.294" (uid=0 pid=2219 comm="/usr/sbin/pppd nodetach lock nodefaultroute ttyUSB") interface="org.freedesktop.NetworkManager.PPP" member="SetState" error name="(unset)" requested_reply=0 destination="org.freedesktop.NetworkManager" (uid=0 pid=25392 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))
May  1 13:13:08 dell1833 dbus-daemon: Rejected send message, 7 matched rules; type="method_call", sender=":1.294" (uid=0 pid=2219 comm="/usr/sbin/pppd nodetach lock nodefaultroute ttyUSB") interface="org.freedesktop.NetworkManager.PPP" member="SetIp4Config" error name="(unset)" requested_reply=0 destination="org.freedesktop.NetworkManager" (uid=0 pid=25392 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))


(times are off because I ran it again)

Kallahar

---

### Post by kallahar on 2009-05-01
Problem solved (though I think I re-opened a security hole)

[http://bbs.archlinux.org/viewtopic.php?pid=543508](http://bbs.archlinux.org/viewtopic.php?pid=543508)

Replacing /etc/dbus-1/system.d/NetworkManager.conf and nm-applet.conf with the ones posted there by MadHatter fixed the problem.

From madhatter's post:

replace NetworkManager.conf with:

<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
        <policy user="root">
                <allow own="org.freedesktop.NetworkManager"/>
                <allow send_destination="org.freedesktop.NetworkManager"/>
                <allow send_interface="org.freedesktop.NetworkManager"/>

        <allow own="org.freedesktop.NetworkManager.PPP"/>
                <allow send_destination="org.freedesktop.NetworkManager.PPP"/>
                <allow send_interface="org.freedesktop.NetworkManager.PPP"/>
        </policy>
    <!-- My hack -->
        <policy group="network">
                <allow send_destination="org.freedesktop.NetworkManager"/>
                <allow send_interface="org.freedesktop.NetworkManager"/>
        </policy>
        <!-- End of my hack -->
        <policy at_console="true">
                <allow send_destination="org.freedesktop.NetworkManager"/>
                <allow send_interface="org.freedesktop.NetworkManager"/>
        </policy>
        <policy context="default">
                <deny own="org.freedesktop.NetworkManager"/>
                <deny send_destination="org.freedesktop.NetworkManager"/>
                <deny send_interface="org.freedesktop.NetworkManager"/>

                <deny own="org.freedesktop.NetworkManager.PPP"/>
                <deny send_destination="org.freedesktop.NetworkManager.PPP"/>
                <deny send_interface="org.freedesktop.NetworkManager.PPP"/>
        </policy>

        <limit name="max_replies_per_connection">512</limit>
</busconfig>



replace nm-applet.conf with:

<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
    <policy user="root">
        <allow own="org.freedesktop.NetworkManagerUserSettings"/>

        <allow send_destination="org.freedesktop.NetworkManagerUserSettings"/>
        <allow send_interface="org.freedesktop.NetworkManagerSettings"/>

        <!-- Only root can get secrets -->
        <allow send_interface="org.freedesktop.NetworkManagerSettings.Secrets"/>
    </policy>
    <!-- My hack -->
    <policy group="network">
        <allow own="org.freedesktop.NetworkManagerUserSettings"/>
        <allow send_destination="org.freedesktop.NetworkManagerUserSettings"/>
        <allow send_interface="org.freedesktop.NetworkManagerUserSettings"/>

        <deny send_interface="org.freedesktop.NetworkManagerSetting.Secrets"/>
    </policy>
       <!-- end of my hack -->
    <policy at_console="true">
        <allow own="org.freedesktop.NetworkManagerUserSettings"/>

        <allow send_destination="org.freedesktop.NetworkManagerUserSettings"/>
        <allow send_interface="org.freedesktop.NetworkManagerSettings"/>

        <!-- Only root can get secrets -->
        <deny send_interface="org.freedesktop.NetworkManagerSettings.Secrets"/>
    </policy>
    <policy context="default">
        <deny own="org.freedesktop.NetworkManagerUserSettings"/>

        <allow send_destination="org.freedesktop.NetworkManagerUserSettings"/>
        <allow send_interface="org.freedesktop.NetworkManagerSettings"/>
        <!-- Only root can get secrets -->
        <deny send_interface="org.freedesktop.NetworkManagerSettings.Secrets"/>
    </policy>

    <limit name="max_replies_per_connection">512</limit>
</busconfig>

---

