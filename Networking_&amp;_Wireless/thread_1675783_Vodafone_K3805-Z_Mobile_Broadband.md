---
title: "Vodafone K3805-Z Mobile Broadband"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by dunbrokin on 2011-01-26
I have hte K3805-Z and am trying to get it to work....it seems to be recognised by the Network Manager....but I am not getting through.

usb-devices yields the following:

T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#= 11 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1003 Rev=00.01
S:  Manufacturer=Vodafone
S:  Product=K3805-z
S:  SerialNumber=C7986D8B72DFB07EF2FAE8645D14803D06F92E84
C:  #Ifs=10 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=02(commc) Sub=08 Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 5 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I:  If#= 6 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I:  If#= 7 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
/usr/bin/usb-devices: line 79: printf: 08: invalid octal number
I:  If#= 0 Alt= 0 #EPs= 0 Cls=02(commc) Sub=0b Prot=00 Driver=(none)
/usr/bin/usb-devices: line 79: printf: 09: invalid octal number
I:  If#= 0 Alt= 0 #EPs= 0 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)

Where do I go from here?

---

### Post by alexfish on 2011-01-26
can have a look at this thread
                     **[Vodafone USB]("http://ubuntuforums.org/showthread.php?t=1669429")**
 
athough a different ID the device looks similar


possible try the script at post    #**[23]("http://ubuntuforums.org/showpost.php?p=10394504&postcount=23")**
 
where it says
    > set Vendor "19d2"
    set Product "1002"change to
    > set Vendor "19d2"
    set Product "1003"this may show the ports but can't confirm .

also can try and find the device produced by lshal
may be something like ttyACM*  or /dev
```

lshal > `pwd`/voda
```

the file should be in home directory
possible find the device ID's

 in the blocks with device ID . also look for lines

linux.sysfs_path =

serial.device =

alexfish

---

### Post by dunbrokin on 2011-01-26
Here is a screen shot.

---

### Post by alexfish on 2011-01-26
HI

yes it shows  a connection.....

could post details of a :how to : would be most helpful to others trying to connect

regards

alexfish

---

### Post by dunbrokin on 2011-01-26
> **alexfish said:**
> HI

yes it shows  a connection.....

could post details of a :how to : would be most helpful to others trying to connect

regards

alexfish

At this stage I have done nothing....this shows when I plug in the device...I still cannot get onto the Mobile Network. The problem is not helped by the fact that I do not have mobile reception here at home.

---

### Post by alexfish on 2011-01-26
hi

from the screen shot it looked as if you had a connection / the image is blurry 

From what I gather your still looking for a solution

as a update from the other thread , there is a post where the device shows tttACM0

could see if there is dev serial ttyACM

can try

```
ls -al /dev/serial/by-id
```if there is a listing at the end with ttyACM0 or others

then the connection path could be /dev/ttyACM0

with this info could try wvdial

but may need other info from the device :  dial command , and or possible the APN

to find the APN's can have a look at this how to

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

ref post #1

only thing of note is that some connection managers rely on getting info about the device settings
as seen by the system , so therefore setting wvdial to use the correct port will overcome
what other connection managers or modem-managers can't do

alexfish

---

### Post by dunbrokin on 2011-01-26
> **alexfish said:**
> hi

from the screen shot it looked as if you had a connection / the image is blurry 

From what I gather your still looking for a solution

as a update from the other thread , there is a post where the device shows tttACM0

could see if there is dev serial ttyACM

can try

```
ls -al /dev/serial/by-id
```if there is a listing at the end with ttyACM0 or others

then the connection path could be /dev/ttyACM0

with this info could try wvdial

but may need other info from the device :  dial command , and or possible the APN

to find the APN's can have a look at this how to

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

ref post #1

only thing of note is that some connection managers rely on getting info about the device settings
as seen by the system , so therefore setting wvdial to use the correct port will overcome
what other connection managers or modem-managers can't do

alexfish

~$ ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 80 2011-01-27 13:08 .
drwxr-xr-x 4 root root 80 2011-01-27 13:08 ..
lrwxrwxrwx 1 root root 13 2011-01-27 13:08 usb-Vodafone_K3805-z_C7986D8B72DFB07EF2FAE8645D14803D06F92E84-if01 -> ../../ttyACM0
lrwxrwxrwx 1 root root 13 2011-01-27 13:08 usb-Vodafone_K3805-z_C7986D8B72DFB07EF2FAE8645D14803D06F92E84-if03 -> ../../ttyACM1

However, I have no idea what this means or where I go from here.

---

### Post by alexfish on 2011-01-27
> **dunbrokin said:**
> ~$ ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 80 2011-01-27 13:08 .
drwxr-xr-x 4 root root 80 2011-01-27 13:08 ..
lrwxrwxrwx 1 root root 13 2011-01-27 13:08 usb-Vodafone_K3805-z_C7986D8B72DFB07EF2FAE8645D14803D06F92E84-if01 -> ../../ttyACM0
lrwxrwxrwx 1 root root 13 2011-01-27 13:08 usb-Vodafone_K3805-z_C7986D8B72DFB07EF2FAE8645D14803D06F92E84-if03 -> ../../ttyACM1

However, I have no idea what this means or where I go from here.
can have a look here

[**Vodafone USB**]("http://ubuntuforums.org/showthread.php?t=1669429")

**RE;post #36** :: can post results back here

alexfish

---

### Post by dunbrokin on 2011-01-27
pj@pj-indulgence:~$ ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 80 2011-01-28 12:43 .
drwxr-xr-x 4 root root 80 2011-01-28 12:43 ..
lrwxrwxrwx 1 root root 13 2011-01-28 12:43 usb-Vodafone_K3805-z_C7986D8B72DFB07EF2FAE8645D14803D06F92E84-if01 -> ../../ttyACM0
lrwxrwxrwx 1 root root 13 2011-01-28 12:43 usb-Vodafone_K3805-z_C7986D8B72DFB07EF2FAE8645D14803D06F92E84-if03 -> ../../ttyACM1
pj@pj-indulgence:~$ tr -s "\n" < /dev/ttyACM0
bash: /dev/ttyACM0: Device or resource busy
pj@pj-indulgence:~$ 

Thanks for your help....I really appreciate it.

---

### Post by dunbrokin on 2011-01-28
The light never comes on on my Vodem.....I am starting to think that this is a wasted effort....has anybody got this to work?

---

### Post by alexfish on 2011-01-29
Hi

need to find out which port is the modem and if any resource is is holding the device

as from the output

> : /dev/ttyACM0: Device or resource busycan post the results of

```
pidof pppd
``````
pidof modem-manager
```can make sure and just kill

```
poff
``````
sudo killall modem-manager
```then try the commands from the thread link

can also see if the device or part of the device shows as a modem

can try this bit of script which will look through the output of the command "lshal"

make the file
```
gedit `pwd`/Desktop/lshal-modem.tcl
```

copy and paste this
```
#!/usr/bin/tclsh
    ################################
    set lshal [exec lshal]
    set lshal [split $lshal "\n"]
    set modem aux:
    foreach lin $lshal {
            set ldfp [string first {'serial', 'modem'} $lin]
            if {$ldfp > -1} {
            puts $lin
            set modem "modem:"
            }
        set ldfp [string first {modem.command_sets} $lin]
            if {$ldfp > -1} {puts $lin}
        set ldfp [string first {serial.device} $lin]
            if {$ldfp > -1} {
            puts "$lin: $modem"
            puts ""
            puts ""
            set modem aux:
            }
    }

```

save and exit

then to exec

```
tclsh `pwd`/Desktop/lshal-modem.tcl
```

post the results

---

### Post by dunbrokin on 2011-01-29
Terminal 1

pj@pj-indulgence:~$ pidof pppd
pj@pj-indulgence:~$ pidof modem-manager
1467
pj@pj-indulgence:~$ poff
/usr/bin/poff: No pppd is running.  None stopped.
pj@pj-indulgence:~$ 
pj@pj-indulgence:~$ tr -s "\n" < /dev/ttyACM0
bash: /dev/ttyACM0: Device or resource busy
pj@pj-indulgence:~$ sudo killall modem-manager
[sudo] password for pj: 
pj@pj-indulgence:~$ tr -s "\n" < /dev/ttyACM0

OK

+CREG: 0

+CGREG: 0

+CREG: 2

+CGREG: 2

+CPIN: READY

OK

P680A5.0.03

OK

+CREG: 0

+CGREG: 0

+COPS: 0

OK

+CREG: 2

+CGREG: 2



Terminal 2

pj@pj-indulgence:~$ echo -e "AT\r" > /dev/ttyACM0
bash: /dev/ttyACM0: Device or resource busy
pj@pj-indulgence:~$ echo -e "AT\r" > /dev/ttyACM0
pj@pj-indulgence:~$ echo -e "AT+CPIN?\r" > /dev/ttyACM0
pj@pj-indulgence:~$ echo -e "ATI\r" > /dev/ttyACM0
pj@pj-indulgence:~$ echo -e "AT+COPS?\r" > /dev/ttyACM0
pj@pj-indulgence:~$

---

### Post by dunbrokin on 2011-01-29
pj@pj-indulgence:~$ tclsh `pwd`/Desktop/lshal-modem.tcl
  info.capabilities = {'serial', 'modem'} (string list)
  modem.command_sets = {'V.250'} (string list)
  serial.device = '/dev/ttyACM1'  (string): modem:


  info.capabilities = {'serial', 'modem'} (string list)
  modem.command_sets = {'V.250'} (string list)
  serial.device = '/dev/ttyACM0'  (string): modem:

---

