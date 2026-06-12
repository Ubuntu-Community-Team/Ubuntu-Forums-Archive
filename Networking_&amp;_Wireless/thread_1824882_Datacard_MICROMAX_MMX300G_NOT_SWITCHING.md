---
title: "Datacard MICROMAX MMX300G NOT SWITCHING"
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by im.saravanan on 2011-08-14
hI friends,

Installed unity 11.04. For the first time when i plug in my micromax mmx 300G datacard i was surprised to see the red LED turn green. The usb modem is switched . and i could connect to interenet. Checked connection info option1 driver was being used image at [http://ubuntuone.com/p/1AHd/](http://ubuntuone.com/p/1AHd/) . My joy was short lived. From the very next time the modem is not switching. command usb-devices shows option driver loaded. Also In my computer there is a storage device icon. I uninstalled the usb-modeswitch and installed the latest release. Still not working. The red LED is not turning green at all.

vid-05c6 pid-f000 before switching. after switching vid-05c6 and pid is 9000.

output of usb-devices for mmx300G is:--

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=05c6 ProdID=9000 Rev=00.00
S:  Manufacturer=Micromax
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

output of dmesg at the end is;---

1683.676556] USB Mass Storage support registered.
[ 1683.951777] usb 1-1: USB disconnect, address 4
[ 1684.296126] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 1684.442011] scsi5 : usb-storage 1-1:1.2
[ 1685.442788] scsi 5:0:0:0: Direct-Access     Micromax MMC Storage      2.31 PQ: 0 ANSI: 2
[ 1685.445621] sd 5:0:0:0: Attached scsi generic sg1 type 0
[ 1685.451985] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 1685.743481] usbcore: registered new interface driver usbserial
[ 1685.743541] USB Serial support registered for generic
[ 1685.746603] usbcore: registered new interface driver usbserial_generic
[ 1685.746612] usbserial: USB Serial Driver core
[ 1685.780381] USB Serial support registered for GSM modem (1-port)
[ 1685.782394] usbcore: registered new interface driver option
[ 1685.782405] option: v0.7.2:USB Driver for GSM modems
[ 1685.795485] option 1-1:1.0: GSM modem (1-port) converter detected
[ 1685.795832] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[ 1685.795972] option 1-1:1.1: GSM modem (1-port) converter detected
[ 1685.796456] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 1685.796629] option 1-1:1.3: GSM modem (1-port) converter detected
[ 1685.796983] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
[ 1868.820443] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
sarvannan@sarvannan-Aspire-one:~$ 

. I am struggling form ubuntu 9.04 to make it work. Can the senior users help me. Does the above output throw some light for you.

---

### Post by im.saravanan on 2011-08-15
Hi firends,

In the forum there are many threads for micromax mmx300g switching, where the problem is solved.

But difference is that the vid is same as mine -05c6 ,whereas the pid is different. mine is f000/9000 before & after switching.

My MMX300g has same vid -05c6 and pid-f000/9000 as Siptune LM-75 ("LinuxModem") in the 40-usb_modeswitch.rules files. that may be the reason for auto switching. But the LED indicator is not turning green from red to confirm the switching.  something somewhere is going wrong. How to find it. Does the message content passed is different? 

I downloaded and installed sakis3g from [www.sakis3g.org](www.sakis3g.org) and installed it. plugged in my winmodem mmx300g and started script sakis3g and  selected it to do the switching, to load module and create tty connections.
It asked me to type the port where tty is created. By seeing the dmesg i gave it as ttyUSB2. after a few second there was a message that modem is set at ttyUSB2. i clicked on the network manager to see the mobile broadband enabled and a new connection created . i clikded on that -wow- the modem light turned green and after a few seconds it was connected to internet. I checked the connection info- the driver loaded is option1. -the port used is GSM(ttyUSB2).

MY QUESTION IS

1.         what did the sakis3g script do that the os could not do.

2. WHAT AND WHERE IS THE BUG?

3. HOW DO WE CORRECT THIS PROBLEM. SO THAT THE OS HANDLES THE ISSUE CORRECTLY.

---

### Post by im.saravanan on 2011-08-15
hi friends,

this is the sakis3g conection report [http://ubuntuone.com/p/1ANa/](http://ubuntuone.com/p/1ANa/)
Initially in sakis3g if i select connect to 3G it would give some error. But it could switch the mode, load modules and create tty connections.

WHAT I DID?

there was no file in /etc/usb-modeswitch.d folder. i created a file 05c6:9000 with the following contents.


########################################################
# MICROMAX mmx 300g 

DefaultVendor= 0x05c6
DefaultProduct=0xf000

TargetVendor=  0x05c6
TargetProduct= 0x9000



MessageContent="5553424312345678000000000000061b000000020000000000000000000000"

NeedResponse=1

CheckSuccess=20

###############################################################

and i edited /etc/modules file to add the following line

#MICROMAX 300G 3G USB MODEM
usbserial vendor=0x05c6 product=0x9000

saved and rebooted the pc.

Plug in the modem, started sakis3g and clicked connect to 3g, it asked for the APN of the Service provided. On giving it connected to interenet. It saved the APN for furture connections also. 

But still could not connect without sakis3g. 

Tried once. In network manager created a new mobile broadband connection , after a few seconds it could sense the Micromax 9000 and asked created a new connection for this devices Micromax 9000 and clicked forward and gave all setting. I could see Mobile broadband connection in network manager. When i clicked connect, the already switched modem turn-off.(unswitched). Tried again. same result.

---

### Post by alexfish on 2011-08-15
Hi im.saravanan

as you noted the usb_modeswitch.d folder is empty . and have entered the correct data for you device
however the option module does not contain this device id's ,the usb_modeswitch may init the device in the option module if it is loaded at boot,should  not need to use the standard usb-serial from the etc/modules (not recommended),try loading the option module, see what happens (also try connecting the device at boot , and also after boot , monitor the results)

sakis3g will try and allocate a suitable driver for the device if no driver module has bound to it.
can always recommend installing sakis3g on an Linux System as a matter of course.

I have done a post in
**Re: Natty, known bugs, fixes and work arounds** Post #[**30**]("http://ubuntuforums.org/showpost.php?p=10793568&postcount=30")  

ADDED
if the new_id fails can use the following script, or use the commands from the terminal

```
#!/bin/sh
modprobe option
echo "05c6 9000" > /sys/bus/usb-serial/drivers/option1/new_id

```regards
alexfish

---

### Post by im.saravanan on 2011-08-16
Hi Alex,

Thanks for your guidance.

The below results were obtained without running the sakis3g script.

I commented the usbserial line in the /etc/modules and restarted the machine.Hi Alex,

Thanks for your guidance.

I commented the usbserial line in the /etc/modules and restarted the machine.

Once  with modem plugged-in before starting the pc. waited for few minutes.  mobile broadband appeared in the network manager menu. with the name of  the connection "Airtel connection". May be it picked up the apn and  other config from the setting which i had given for bluetooth mobile  broadband for nokia mobile .
when i clicked to connect. it unswitched  my modem . Green led turned Red. Same thing happened when i plugged in  the modem after starting the machine. 

then in terminal  i tried to run the scripts in your reply. the output was something like -"No such directory or file"

Next in the Terminal I gave the command

$sudo /usr/sbin/update-usbids

It updated something from [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)

Then i restarted the machine,

Inserted the modem the led turned green indicating switching. opened the terminal and gave the command

$nm-tools

ttyUSB  or Mobile Broadband was not shown only etho & wlan0 was shown in  the output. gave the same command again and again. after 2 minutes it  recognized . This time it also included the below lines.

#################################################################################

Device: ttyUSB2 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             disconnected
  Default:           no

  Capabilities:
##################################################################################

In the network manager when i clicked on the mobile broadband -Airtel connection. It got connected to internet.

###################################################################################
 Device: ttyUSB2  [Airtel connection] -----------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         223.190.239.244
    Prefix:          32 (255.255.255.255)
    Gateway:         10.64.64.65

    DNS:             202.56.230.5
    DNS:             202.56.230.6
####################################################################################

I disconnected & connected agian . it got connected immediately.

I think the command to update-subids did the magic, Can u tell me what actually the update-usbids command do.

Needs Improvement for the below issues

But one thing - i must always wait for 2 minutes for the mobile broadband to show up the nm-tool before connecting.

And   - from the time i plug in the modem to the time it is shown in nm-tool ,  the machine becomes very slow, like hanging for 10 sec working for 5sec  alternatively.

---

### Post by xlearner on 2011-11-29
I have a similar problem. I am using Ubuntu 10.10. I have Micromax MMX 310G USB Modem with a bsnl 3G SIM Card. I created a new mobile broadband connection. When I try to plug-in the device, it is not showing a new network connection. So I am unable to connect to it at all. 

I posted the same problem on a similar thread as well: [http://ubuntuforums.org/showthread.php?t=1695102](http://ubuntuforums.org/showthread.php?t=1695102)

I downloaded Sakis 3G utility. Unfortunately, it did not work as well. It is failing after when "switching to the modem". I was getting the error message, "Failed to Connect".
Then I looked into 'more options'. There when I click on 'Only switch modem' option, it returns successfully with the message "Modem switched to 1c9e:f000". But when I click on 'Only setup modem (Switch + Load Module + Setup tty)', it fails with the message "Failed to setup modem".

So can anyone help me or give me some advice?

Thanks

---

### Post by im.saravanan on 2011-12-04
HI XLEARNER,

you have not stated whether your modem gets switched. i mean the led light indication. 

when  insert the modem , initially the led is red and then it changes color indicating switching. Tell me if this happens in your case. 
Now a days bsnl 3g modem comes with a script in the modem, which gets installed on first time and then option comes in application menu.
application menu->Connect/Disconnect.

which you can use .

---

### Post by xlearner on 2011-12-10
Dear im.sarvanan,

Thanks a lot for your reply. Coming to your question, I think the modem is switching. It was initially red in color. Then it changes to blue color. But there was no script that was getting installed with the modem. S0 there was nothing that I could use here. Any other suggestions? 

Thanks
Xlearner

---

