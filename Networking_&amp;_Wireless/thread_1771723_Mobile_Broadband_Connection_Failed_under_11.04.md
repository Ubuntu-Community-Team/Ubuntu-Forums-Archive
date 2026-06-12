---
title: "Mobile Broadband Connection Failed under 11.04"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by mikhailmv on 2011-05-30
I use Nokia N900 under T-Mobile as a broadband modem. It is connected via USB.
There was no connection problems under 10.04 or 10.10.
Now I have installed Ubuntu 11.04, and I cannot connect any more.

Here are the log messages that I get when trying to connect:
```

May 30 14:32:06 ubuntu-sager NetworkManager[759]: <info> Activation (ttyACM0) starting connection 'T-Mobile Internet'
May 30 14:32:06 ubuntu-sager NetworkManager[759]: <info> (ttyACM0): device state change: 3 -> 4 (reason 0)
May 30 14:32:06 ubuntu-sager NetworkManager[759]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
May 30 14:32:06 ubuntu-sager NetworkManager[759]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
May 30 14:32:06 ubuntu-sager NetworkManager[759]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
May 30 14:32:06 ubuntu-sager modem-manager[766]: <info>  (ttyACM0) opening serial port...
May 30 14:32:06 ubuntu-sager modem-manager[766]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
May 30 14:32:10 ubuntu-sager modem-manager[766]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> disabled)
May 30 14:32:10 ubuntu-sager modem-manager[766]: <info>  (ttyACM0) closing serial port...
May 30 14:32:10 ubuntu-sager modem-manager[766]: <info>  (ttyACM0) serial port closed
May 30 14:32:10 ubuntu-sager NetworkManager[759]: <warn> GSM modem enable failed: (32) Serial command timed out
May 30 14:32:10 ubuntu-sager NetworkManager[759]: <info> (ttyACM0): device state change: 4 -> 9 (reason 28)
May 30 14:32:10 ubuntu-sager NetworkManager[759]: <info> Marking connection 'T-Mobile Internet' invalid.
May 30 14:32:10 ubuntu-sager NetworkManager[759]: <warn> Activation (ttyACM0) failed.
May 30 14:32:10 ubuntu-sager NetworkManager[759]: <info> (ttyACM0): device state change: 9 -> 3 (reason 0)
May 30 14:32:10 ubuntu-sager NetworkManager[759]: <info> (ttyACM0): deactivating device (reason: 0).

```

---

### Post by happy_heyoka on 2011-06-02
I have exactly the same problem (N900 on a USB cable to either of two boxes running Natty Kubuntu - vodafone network) and have only seen problems since I upgraded (I upgraded using another connection).

I have had one or two successful connections out of dozens of tries.

At the moment I am connected using the setup - but it was only after I killed the NetworkManager and modem-manager processes and started them up in debug mode - I suspect this altered the timing of the connection process somehow...

(connection log prior to debug mode)
[FONT=Courier New][SIZE=1]02/06/11 08:56:08 PM    box    NetworkManager[549]    <info> Activation (ttyACM0) starting connection 'vodafone mobile internet'
02/06/11 08:56:08 PM    box    NetworkManager[549]    <info> (ttyACM0): device state change: 3 -> 4 (reason 0)
02/06/11 08:56:08 PM    box    NetworkManager[549]    <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
02/06/11 08:56:08 PM    box    NetworkManager[549]    <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
02/06/11 08:56:08 PM    box    NetworkManager[549]    <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
02/06/11 08:56:08 PM    box    modem-manager[585]    <info>  (ttyACM0) opening serial port...
02/06/11 08:56:08 PM    box    modem-manager[585]    <info>  Modem /org/freedesktop/ModemManager/Modems/1: state changed (disabled -> enabling)
02/06/11 08:56:11 PM    box    modem-manager[585]    <info>  Modem /org/freedesktop/ModemManager/Modems/1: state changed (enabling -> disabled)
02/06/11 08:56:11 PM    box    modem-manager[585]    <info>  (ttyACM0) closing serial port...
02/06/11 08:56:11 PM    box    modem-manager[585]    <info>  (ttyACM0) serial port closed
02/06/11 08:56:11 PM    box    NetworkManager[549]    <warn> GSM modem enable failed: (32) Serial command timed out
02/06/11 08:56:11 PM    box    NetworkManager[549]    <info> (ttyACM0): device state change: 4 -> 9 (reason 28)
02/06/11 08:56:11 PM    box    NetworkManager[549]    <info> Marking connection 'vodafone mobile internet' invalid.
02/06/11 08:56:11 PM    box    NetworkManager[549]    <warn> Activation (ttyACM0) failed.
02/06/11 08:56:11 PM    box    NetworkManager[549]    <info> (ttyACM0): device state change: 9 -> 3 (reason 0)
02/06/11 08:56:11 PM    box    NetworkManager[549]    <info> (ttyACM0): deactivating device (reason: 0).
[/SIZE][/FONT]
(connection log while in debug mode)
[FONT=Courier New][SIZE=1]02/06/11 09:28:21 PM    box    NetworkManager[3947]    <info> Activation (ttyACM0) starting connection 'vodafone mobile internet'
02/06/11 09:28:21 PM    box    NetworkManager[3947]    <info> (ttyACM0): device state change: 3 -> 4 (reason 0)
02/06/11 09:28:21 PM    box    NetworkManager[3947]    <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
02/06/11 09:28:21 PM    box    NetworkManager[3947]    <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
02/06/11 09:28:21 PM    box    NetworkManager[3947]    <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
02/06/11 09:28:21 PM    box    modem-manager[3888]    <debug> [1307014101.892868] [mm-generic-gsm.c:4362] simple_connect(): (ttyACM0): number => "*99#"
02/06/11 09:28:21 PM    box    modem-manager[3888]    <debug> [1307014101.892914] [mm-generic-gsm.c:4362] simple_connect(): (ttyACM0): network_mode => 0
02/06/11 09:28:21 PM    box    modem-manager[3888]    <debug> [1307014101.892934] [mm-generic-gsm.c:4362] simple_connect(): (ttyACM0): apn => "vfinternet.au"
02/06/11 09:28:21 PM    box    modem-manager[3888]    <debug> [1307014101.892955] [mm-generic-gsm.c:4362] simple_connect(): (ttyACM0): allowed_mode => 0
02/06/11 09:28:21 PM    box    modem-manager[3888]    <debug> [1307014101.892983] [mm-generic-gsm.c:4251] simple_state_machine(): (ttyACM0): simple connect state 0
02/06/11 09:28:21 PM    box    modem-manager[3888]    <debug> [1307014101.893052] [mm-generic-gsm.c:4251] simple_state_machine(): (ttyACM0): simple connect state 2
02/06/11 09:28:21 PM    box    modem-manager[3888]    <debug> [1307014101.893117] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT+CREG?<CR>'
02/06/11 09:28:21 PM    box    modem-manager[3888]    <debug> [1307014101.943154] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- 'AT+CREG?'
02/06/11 09:28:21 PM    box    modem-manager[3888]    <debug> [1307014101.944378] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '<CR>'
02/06/11 09:28:21 PM    box    modem-manager[3888]    <debug> [1307014101.948363] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '<CR><LF>+CREG: 0,1<CR><LF><CR><LF>OK<CR><LF>'
02/06/11 09:28:21 PM    box    modem-manager[3888]    <debug> [1307014101.948469] [mm-generic-gsm.c:4251] simple_state_machine(): (ttyACM0): simple connect state 4
02/06/11 09:28:21 PM    box    modem-manager[3888]    <debug> [1307014101.948533] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT+CGDCONT?<CR>'
02/06/11 09:28:22 PM    box    modem-manager[3888]    <debug> [1307014102.011345] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- 'AT+CGDCONT?<CR><CR><LF>+CGDCONT: 1,"IP",,,0,0<CR><LF><CR><LF>OK<CR><LF>'
02/06/11 09:28:22 PM    box    modem-manager[3888]    <debug> [1307014102.011552] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT+CGDCONT=1,"IP","vfinternet.au"<CR>'
02/06/11 09:28:22 PM    box    modem-manager[3888]    <debug> [1307014102.183952] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- 'AT+CGDCONT=1,"IP","vfinternet.au"<CR><CR><LF>OK<CR><LF>'
02/06/11 09:28:22 PM    box    modem-manager[3888]    <debug> [1307014102.184069] [mm-generic-gsm.c:4251] simple_state_machine(): (ttyACM0): simple connect state 5
02/06/11 09:28:22 PM    box    modem-manager[3888]    <info>  [1307014102.184221] [mm-modem.c:761] mm_modem_set_state(): Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
02/06/11 09:28:22 PM    box    modem-manager[3888]    <debug> [1307014102.184286] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'ATD*99***1#<CR>'
02/06/11 09:28:22 PM    box    modem-manager[3888]    <debug> [1307014102.245200] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- 'ATD*99***1#<CR>'
02/06/11 09:28:23 PM    box    modem-manager[3888]    <debug> [1307014103.760416] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '<CR><LF>CONNECT<CR><LF>'
02/06/11 09:28:23 PM    box    modem-manager[3888]    <debug> [1307014103.760543] [mm-port.c:181] mm_port_set_connected(): (ttyACM0): port now connected
02/06/11 09:28:23 PM    box    modem-manager[3888]    <info>  [1307014103.760699] [mm-modem.c:761] mm_modem_set_state(): Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> connected)
02/06/11 09:28:23 PM    box    modem-manager[3888]    <debug> [1307014103.760758] [mm-generic-gsm.c:4251] simple_state_machine(): (ttyACM0): simple connect state 6
02/06/11 09:28:23 PM    box    NetworkManager[3947]    <info> Activation (ttyACM0) Stage 2 of 5 (Device Configure) scheduled...
02/06/11 09:28:23 PM    box    NetworkManager[3947]    <info> Activation (ttyACM0) Stage 2 of 5 (Device Configure) starting...
02/06/11 09:28:23 PM    box    NetworkManager[3947]    <info> (ttyACM0): device state change: 4 -> 5 (reason 0)
02/06/11 09:28:23 PM    box    modem-manager[3888]    <debug> [1307014103.764399] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '~\255}#\192!}!} } }2}#}$\192#}!}$}%\220}"}&} }*} } g}%~'
02/06/11 09:28:23 PM    box    NetworkManager[3947]    <info> Activation (ttyACM0) Stage 2 of 5 (Device Configure) successful.
02/06/11 09:28:23 PM    box    NetworkManager[3947]    <info> Activation (ttyACM0) Stage 3 of 5 (IP Configure Start) scheduled.
02/06/11 09:28:23 PM    box    NetworkManager[3947]    <info> Activation (ttyACM0) Stage 2 of 5 (Device Configure) complete.
02/06/11 09:28:23 PM    box    NetworkManager[3947]    <info> Activation (ttyACM0) Stage 3 of 5 (IP Configure Start) started...
02/06/11 09:28:23 PM    box    NetworkManager[3947]    <info> (ttyACM0): device state change: 5 -> 7 (reason 0)
02/06/11 09:28:23 PM    box    NetworkManager[3947]    <info> starting PPP connection
02/06/11 09:28:23 PM    box    NetworkManager[3947]    <info> pppd started with pid 4076
02/06/11 09:28:23 PM    box    NetworkManager[3947]    <info> Activation (ttyACM0) Stage 3 of 5 (IP Configure Start) complete.
02/06/11 09:28:23 PM    box    pppd[4076]    Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
02/06/11 09:28:23 PM    box    pppd[4076]    pppd 2.4.5 started by root, uid 0
02/06/11 09:28:23 PM    box    modem-manager[3888]    <debug> [1307014103.787595] [mm-manager.c:786] device_added(): (net/ppp0): could not get port's parent device
02/06/11 09:28:23 PM    box    NetworkManager[3947]       SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
02/06/11 09:28:23 PM    box    NetworkManager[3947]       SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
02/06/11 09:28:23 PM    box    pppd[4076]    Using interface ppp0
02/06/11 09:28:23 PM    box    pppd[4076]    Connect: ppp0 <--> /dev/ttyACM0
[/SIZE][/FONT](etc...)

---

### Post by happy_heyoka on 2011-06-03
Just replying to my self: modem-manager doesn't have to be in debug mode, but NetworkManager does, with NM_PPP_DEBUG=1

---

### Post by Krank on 2011-06-03
Same problem here. Tethering using a Nokia N900 on an Asus EEE 900, and Ubuntu 11.04. Worked just fine in 10.10 and 10.04. Same error, as well.


Whenever I try to kill the modem-manager or the networkmanager, they seem to immediately restart themselves, making it kinf of hard to launch them manually...

Could you please give me a hint as to the commands you're using? I'm by no means a Linux noob, though I certainly feel like one at the moment...

---

### Post by Krank on 2011-06-03
"Fixed" this by cheating; installed the modem-manager package from Maverick. Now all I need to do is disable wireless, click my "Telia" entry in the network manager menu, and wait a few seconds - and it works.

Ugly workaround, would of course prefer a bugfix... But it'll serve for now.

---

### Post by AcerLaura on 2011-06-04
I wonder how many folk who connect to the net with mobile broadband are now running a mile from Ubuntu 11.04, Linux for mr average? - You can't even get online with the thing! 
I found an easier fix, it's called 10.04 :)
Dare i mention all those updates to come; never mind the time installing them.
Changed my mind. I recommend MicroXP :)

---

### Post by happy_heyoka on 2011-06-06
@AcerLaura - you make the mistake of assuming that the people who put together Ubuntu are the only ones involved in creating and maintaining the modem-manager...  Feel free to vent, but don't expect it to help much.

Of course, you could always pitch in and help.

---

### Post by happy_heyoka on 2011-06-06
> **Krank said:**
> "Fixed" this by cheating; installed the modem-manager package from Maverick. Now all I need to do is disable wireless, click my "Telia" entry in the network manager menu, and wait a few seconds - and it works.

Ugly workaround, would of course prefer a bugfix... But it'll serve for now.

That works for me too...

However, it makes me wonder about something.  Pay attention to the next time you plug in your N900 - does your first connection attempt fail, and then the second one work.

I noticed this in the change log for the modem-manager as shipped with 11.04 :

>     *- nokia: N900 appears to need a longer port delay (rh #583691)*

I suspect this is a mis-diagnosis of the problem - it's not a timing thing, it's a synchronisation thing and either the PC or the N900 is waiting for some more data.  I'll see what I can do about a bug report.

---

### Post by happy_heyoka on 2011-06-06
> **Krank said:**
> Whenever I try to kill the modem-manager or the networkmanager, they seem to immediately restart themselves, making it kinf of hard to launch them manually...

Could you please give me a hint as to the commands you're using? I'm by no means a Linux noob, though I certainly feel like one at the moment...

Yes, the Network Manager appears to relaunch the Modem Manager if it goes away... so, just for completeness, here's how.

First open up a console window and stop the network manager service:

[FONT=Courier New][COLOR=Green]**~$**[/COLOR] sudo service network-manager stop[/FONT]


next, kill the modem manager:

[FONT=Courier New][COLOR=Green]**~$**[/COLOR] ps -A | grep modem
[COLOR=Green]  775 ?        00:00:00 modem-manager[/COLOR]
 
[COLOR=Green]**~$**[/COLOR] sudo kill 775
[COLOR=Green]**~$**[/COLOR] ps -A | grep modem[/FONT]
*(no output = good, modem-manager gone)*

open a *second* console window and restart the modem manager in debug mode
[FONT=Courier New]
[COLOR=Green]**~$**[/COLOR] sudo modem-manager --debug[/FONT]
*(debug output from modem manager)*


go back to the *first* console window and restart the network manager

[FONT=Courier New][COLOR=Green]**~$**[/COLOR] NM_PPP_DEBUG=1
[COLOR=Green]**~$**[/COLOR] sudo NetworkManager --no-daemon[/FONT]
*(debug output from network manager)*

---

### Post by jhilden on 2011-06-11
I have the same problem with the same error message as the one in the top post.

Running network-manager and modem-manager in debug mode worked for me, but is there a *real* fix in sight anywhere?  Is there a bug filed in the appropriate place already?

---

### Post by jhilden on 2011-06-11
Here is the Ubuntu bug:
[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/765516](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/765516)

But it doesn't look like it has been figured out how to fix this yet :(

---

### Post by Krank on 2011-06-11
> **AcerLaura said:**
> Changed my mind. I recommend MicroXP :)

Umh, yeah... I'm dualbooting XP, and tethering is a bleeding nightmare there, since I need to use Nokias bloatware (OVI) to do it. While Ubuntu manages more or less out of the box.

Installing old version of modem-manager is <1mb. Installing OVI... Well, it's an 87 mb download...

---

### Post by Krank on 2011-06-11
> **happy_heyoka said:**
> However, it makes me wonder about something.  Pay attention to the next time you plug in your N900 - does your first connection attempt fail, and then the second one work.

Nope; my N900 either does not connect at all (new modem-manager) or connects just fine (old modem-manager). No in-betweens...

---

### Post by MMN-o on 2011-06-18
> **Krank said:**
> Nope; my N900 either does not connect at all (new modem-manager) or connects just fine (old modem-manager). No in-betweens...

I cannot connect if I try to use the PC Suite Mode and usb modem function _after_ entering the PIN code on the N900.

However if I boot the N900 without enabling the SIM card with a pin, and instead do this through Network Manager, I have no problem using NM in Ubuntu 11.04


Update: The bug report for this problem presents a workaround. At least I get it working if I connect _before_ entering PIN code on the N900 (i.e. let Ubuntu/Network Manager pass it along). [https://bugs.launchpad.net/modemmanager/+bug/765516/comments/9](https://bugs.launchpad.net/modemmanager/+bug/765516/comments/9)

---

### Post by juise- on 2011-08-13
Hi all!

After fighting with this issue again a couple of hours, I wanted to let you know that I'm getting good results doing following (so far 100%):

1) Connect N900 with USB
2) Select 'PC Suite' mode in N900
3) In terminal, do 'sudo modprobe -r cdc_acm; sudo modprobe cdc_acm'
4) Wait a few seconds for the driver to re-initialize
5) Connecting should work now.

My short diagnosis is, that the cdc_acm driver starts initializing the ACM device too fast (before one gets a chance to set the 'PC Suite' mode on N900) and leaves it in unworking state. Forcing driver reinitialization after 'PC Suite' mode is active seems to make it to work.

FWIW, I'm using Kubuntu 11.04.

---

### Post by tpievila on 2011-09-06
Thanks for the modprobe hint! That "solves" it. I hate these regressions, especially when they bite you when you DON'T have any other Internet connection...

---

