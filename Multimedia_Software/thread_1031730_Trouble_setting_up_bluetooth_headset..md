---
title: "Trouble setting up bluetooth headset."
date: 2009-01-05
forum: Multimedia Software
---

### Post by TremerePuck on 2009-01-05
I can't get my bluetooth headset to work at all. The most I can get is a hiss at the beginning of testing a song after downgrading to bluez3.

This is driving me crazy and any help is appreciated.

---

### Post by IQRules on 2009-01-05
Here are the steps for set up Microsoft mouse.

1. $ hcitool scan
2. Press Connect Channel button from your device
3. Obtain Device ID from step 1, like  00:50:F2:E3:5B:AA 
4. sudo bash -- to root account
5. Add this to /etc/default/bluetooth
HID2HCI_ENABLED=1
HID2HCI_UNDO=1
HIDD_OPTIONS="--master --server"
HIDD_OPTIONS="-i --connect 00:50:F2:E3:5B:AA --server"

6. At line 167, /etc/init.d/bluetooth, add this,
        log_end_msg 0

**[COLOR="Red"]        hciconfig hci0 pscan[/COLOR]**
    ;;
  stop)
        log_daemon_msg "Stopping $DESC"
7. Add this file, /etc/bluetooth/hcid.conf
# cat hcid.conf
device 00:50:F2:E3:5B:AA	{
       name "Microsoft Mouse";
}
8. # /etc/init.d/bluetooth restart
9. In some case, you need to remove the device from the top bluetooth icon drop down.

Is it clear?

---

### Post by TremerePuck on 2009-01-07
On restarting bluetooth service I get

Can't set scan mode on hci0: Network is down (100)

---

