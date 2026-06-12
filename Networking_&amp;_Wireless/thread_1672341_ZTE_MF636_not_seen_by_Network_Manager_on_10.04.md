---
title: "ZTE MF636 not seen by Network Manager on 10.04"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by Darius_ on 2011-01-20
Hi,
I am trying to use a ZTE MF636 (Telstra Australia) USB dongle.

It is detected by the kernel and works in wvdial, however nm doesn't see it so I can't configure it that way.

udevadm info --export-db shows..

P: /devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.3/ttyUSB2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.3/ttyUSB2
E: DRIVER=option1
E: SUBSYSTEM=usb-serial

P: /devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.3/ttyUSB2/tty/ttyUSB2
N: ttyUSB2
S: char/188:2
S: serial/by-path/pci-0000:00:1d.7-usb-0:7:1.3-port0
S: serial/by-id/usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P673C3TBPD010000-if03-port0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.3/ttyUSB2/tty/ttyUSB2
E: MAJOR=188
E: MINOR=2
E: DEVNAME=/dev/ttyUSB2
E: SUBSYSTEM=tty
E: ID_PORT=0
E: ID_PATH=pci-0000:00:1d.7-usb-0:7:1.3
E: ID_VENDOR=ZTE_Incorporated
E: ID_VENDOR_ENC=ZTE\x2cIncorporated
E: ID_VENDOR_ID=19d2
E: ID_MODEL=ZTE_WCDMA_Technologies_MSM
E: ID_MODEL_ENC=ZTE\x20WCDMA\x20Technologies\x20MSM
E: ID_MODEL_ID=0031
E: ID_REVISION=0000
E: ID_SERIAL=ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P673C3TBPD010000
E: ID_SERIAL_SHORT=P673C3TBPD010000
E: ID_TYPE=generic
E: ID_BUS=usb
E: ID_USB_INTERFACES=:ffffff:080650:
E: ID_USB_INTERFACE_NUM=03
E: ID_USB_DRIVER=option
E: ID_IFACE=03
E: ID_VENDOR_FROM_DATABASE=ONDA Communication S.p.A.
E: ID_MODEL_FROM_DATABASE=ZTE MF110/MF636
E: ID_MM_ZTE_PORT_TYPE_MODEM=1E: DEVLINKS=/dev/char/188:2 /dev/serial/by-path/pci-0000:00:1d.7-usb-0:7:1.3-port0 /dev/serial/by-i
d/usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P673C3TBPD010000-if03-port0

lshal shows..

udi = '/org/freedesktop/Hal/devices/usb_device_19d2_31_P673C3TBPD010000_if3_serial_usb_0'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_19d2_31_P673C3TBPD010000_if3'  (string)
  info.product = 'ZTE MF636'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_19d2_31_P673C3TBPD010000_if3_serial_usb_0'  (string)
  linux.device_file = '/dev/ttyUSB2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.3/ttyUSB2/tty/ttyUSB2'  (string)
  serial.device = '/dev/ttyUSB2'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/usb_device_19d2_31_P673C3TBPD010000_if3'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'usb'  (string)

I note that (unlike a different USB 3g modem I have) there is no 'modem' in the capability list.

What is the right way to correct this? Is udev not putting the right hint on for hal or is it that a hal rule is missing? (or something else :)

Thanks!

---

### Post by alexfish on 2011-01-21
Hi

It  could be the modem-manager possible try using NetworkManager daily

[SIZE=2][B][http://ubuntuforums.org/showthread.php?t=1549395](http://ubuntuforums.org/showthread.php?t=1549395)

[/B][/SIZE]but notice that the modem is a wcdma , and modem-manager may need  info plugin for some devices

so could not guarantee daily would work 

alexfish

---

### Post by Darius_ on 2011-01-22
I created /etc/hal/fdi/information/10-zte-626i.fdi with the contents
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- xml -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.category" string="serial">
      <match key="@info.parent:usb.vendor_id" int="0x19d2">
        <!-- ZTE MF626i HSDPA USB dongle -->
        <match key="@info.parent:usb.product_id" int="0x0031">
          <match key="@info.parent:usb.interface.number" int="3">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
            <append key="info.capabilities" type="strlist">modem</append>
          </match>
        </match>
      </match>
    </match>
  </device>
</deviceinfo>

```

And now lshal shows..

```

udi = '/org/freedesktop/Hal/devices/usb_device_19d2_31_P673C3TBPD010000_if0_serial_usb_0'
  info.capabilities = {'serial', 'modem'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_19d2_31_P673C3TBPD010000_if0'  (string)
  info.product = 'ZTE MF110/MF636'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_19d2_31_P673C3TBPD010000_if0_serial_usb_0'  (string)
  linux.device_file = '/dev/ttyUSB0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0/ttyUSB0/tty/ttyUSB0'  (string)
  modem.command_sets = {'GSM-07.07', 'GSM-07.05'} (string list)
  serial.device = '/dev/ttyUSB0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/usb_device_19d2_31_P673C3TBPD010000_if0'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'usb'  (string)

```

ie it now has the modem capability.

However NM still doesn't see it as a modem (I restarted it) :(

---

### Post by Darius_ on 2011-01-24
After some debugging under instruction from dcbw from #nm I found that when modem manager probes the device after it appears the SIM is not ready.

ie..

```

** Message: (ttyUSB0) opening serial device...
** (modem-manager:29239): DEBUG: (ttyUSB0): probe requested by plugin 'ZTE'
** Message: (ttyUSB1) opening serial device...
** (modem-manager:29239): DEBUG: (ttyUSB1): probe requested by plugin 'ZTE'
** Message: (ttyUSB2) opening serial device...
** (modem-manager:29239): DEBUG: (ttyUSB2): probe requested by plugin 'ZTE'
** Message: (ttyUSB3) opening serial device...
** (modem-manager:29239): DEBUG: (ttyUSB3): probe requested by plugin 'ZTE'
** (modem-manager:29239): DEBUG: (ttyUSB0): --> 'ATE0+CPMS?<CR>'
** (modem-manager:29239): DEBUG: (ttyUSB1): --> 'ATE0+CPMS?<CR>'
** (modem-manager:29239): DEBUG: (ttyUSB2): --> 'ATE0+CPMS?<CR>'
** (modem-manager:29239): DEBUG: (ttyUSB3): --> 'ATE0+CPMS?<CR>'
** (modem-manager:29239): DEBUG: (ttyUSB1): <-- 'ATE0+CPMS?<CR><CR><LF>ERROR<CR><LF>'
** (modem-manager:29239): DEBUG: Got failure code 100: Unknown error
** (modem-manager:29239): DEBUG: (ttyUSB2): <-- '<CR><LF>ERROR<CR><LF>'
** (modem-manager:29239): DEBUG: Got failure code 100: Unknown error
** (modem-manager:29239): DEBUG: (ttyUSB1): --> 'ATE0+CPMS?<CR>'
** (modem-manager:29239): DEBUG: (ttyUSB2): --> 'ATE0+CPMS?<CR>'
** (modem-manager:29239): DEBUG: (ttyUSB0): --> 'ATE0+CPMS?<CR>'
** (modem-manager:29239): DEBUG: (ttyUSB1): <-- '<CR><LF>ERROR<CR><LF>'
** (modem-manager:29239): DEBUG: Got failure code 100: Unknown error
** (modem-manager:29239): DEBUG: (ttyUSB2): <-- '<CR><LF>ERROR<CR><LF>'
** (modem-manager:29239): DEBUG: Got failure code 100: Unknown error
** (modem-manager:29239): DEBUG: (ttyUSB1): --> 'ATE0+CPMS?<CR>'
** (modem-manager:29239): DEBUG: (ttyUSB2): --> 'ATE0+CPMS?<CR>'
** (modem-manager:29239): DEBUG: (ttyUSB1): <-- '<CR><LF>ERROR<CR><LF>'
** (modem-manager:29239): DEBUG: Got failure code 100: Unknown error
** (modem-manager:29239): DEBUG: (ttyUSB2): <-- '<CR><LF>ERROR<CR><LF>'
** (modem-manager:29239): DEBUG: Got failure code 100: Unknown error
** (modem-manager:29239): DEBUG: (ttyUSB1): --> 'ATE0+CPMS?<CR>'
** (modem-manager:29239): DEBUG: (ttyUSB2): --> 'ATE0+CPMS?<CR>'
** (modem-manager:29239): DEBUG: (ttyUSB3): --> 'ATE0+CPMS?<CR>'
** (modem-manager:29239): DEBUG: (ttyUSB1): <-- '<CR><LF>+CME ERROR: SIM busy<CR><LF>'
** (modem-manager:29239): DEBUG: (ttyUSB2): <-- '<CR><LF>+CME ERROR: SIM busy<CR><LF>'
** (modem-manager:29239): DEBUG: (ttyUSB0): --> 'ATE0+CPMS?<CR>'
** Message: (ttyUSB1) closing serial device...
** Message: (ttyUSB2) closing serial device...
** (modem-manager:29239): DEBUG: (ttyUSB3): --> 'ATE0+CPMS?<CR>'
** (modem-manager:29239): DEBUG: (ttyUSB0): --> 'ATE0+CPMS?<CR>'
** (modem-manager:29239): DEBUG: (ttyUSB3): --> 'ATE0+CPMS?<CR>'
** Message: (ttyUSB0) closing serial device...
** Message: (ttyUSB3) closing serial device...

```

I think this was fixed in this commit [http://cgit.freedesktop.org/ModemManager/ModemManager/commit/?id=95dd4b5be1ebb0408be6e282eb20e2c45df1f253](http://cgit.freedesktop.org/ModemManager/ModemManager/commit/?id=95dd4b5be1ebb0408be6e282eb20e2c45df1f253)

but the MM package is very old and doesn't include it.

A work around is to wait until MM probes the device after insertion and then kill it and it will retry and the SIM will be ready.

---

### Post by alexfish on 2011-01-24
hi

if the device is recognized /and is a 3g device

could try **[*Sakis3G* - All-in-one script]("http://www.sakis3g.org/")**

---

### Post by Brizvegan on 2011-01-25
Hello,

I am a linux newbie experimenting with Ubuntu 10.04 and Linux Mint 9 and 10 in Virtualbox within Windows XP.

I am using the Telstra Elite pre-paid mobile broadband usb modem ZTE MF668 as my only connection to the internet.

Curiously, if I enter "lsusb" in the terminal the modem reads as:

Bus 001 Device 006: ID 19d2:0031 ONDA Communication S.p.A. ZTE [COLOR=Red]MF636[/COLOR]
Bus 001 Device 002: ID 80ee:0021
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I have struggled for about a month with Network Manager and modemmanager, rarely having any success, except for the initial install and set up of the new connection, or when using the live cd.  When I rebooted, it could not connect.

Usually, when I right-click the Network Manager icon, the "Enable mobile broadband" option isn't there most times no matter how long I wait for it to appear.  I think modemmanager is somehow interfering with the process (???)  I have also at various times tried "stopping", "killing", "ending" the modemmanager process and THEN trying to connect, with varying degrees of success.

In Linux Mint 10 I uninstalled modemmanager - it seemed to work better.
However, I have it still installed in Ubuntu 10.04.

I have also connected successfully (sometimes) with Wvdial.  I also tried usb-modeswitch on it own and lots of other suggestions I read in these forums!!!

After reading alexfish's posts I checked out Sakis3g.

Here's my adventure so far with Linux Mint 10 and Sakis3g:
[http://forum.sakis3g.org/smf/index.php?topic=434.0](http://forum.sakis3g.org/smf/index.php?topic=434.0)

It doesn't connect for me always first go, but it is consistently more reliable than anything else in my (very) limited experience.  YMMV ;)

I would definitely recommend trying Sakis3g to anyone who is having problems with these modems.

Cheers,
Brizvegan

---

