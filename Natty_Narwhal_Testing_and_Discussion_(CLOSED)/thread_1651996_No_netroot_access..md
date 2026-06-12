---
title: "No netroot access."
date: 2010-12-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-12-24
My Ethernet card seems to shut itself down when i enter recovery mode. I am trying to update my system which is hung on flashing gdm. I have tried dhclinet eth0 with no luck. I see my wifi indicator turning off as i boot into recovery. I am using Dell Inspiron E1505.

Thanks.

---

### Post by dino99 on 2010-12-24
boot on recovery mode, then select "repair packages" and finally choose "continue normal boot"

---

### Post by efflandt on 2010-12-24
He probably cannot do "repair packages" with no network.

When you set up whichever network connection with network manager did you check "Connect automatically" (usually a default) and "Available to all users" (maybe not a default).  Network settings are in /etc/NetworkManager/system-connections/

Where I only have one connection in Natty, "Auto eth0" only contains (first line blank):


```

[802-3-ethernet]
mac-address=a4:ba:db:f8:d5:a1

[connection]
id=Auto eth0
uuid=e2bd6b42-0ae5-408e-aa12-c72cde0005d7
type=802-3-ethernet
timestamp=1293208113
```On a Lucid system with both eth0 and wireless there are additional sections in both files, but there is also another line in [connection] section which apparently allows either to autoconnect if it has a connection.  So for either your ethernet or wireless file (or both) you might insert the extra line before the timestamp. [B]

sudo nano /etc/NetworkManager/system-connections/Auto\ eth0[/B] or whatever your wireless is called (you do not have to use sudo from root shell, but you do need to escape spaces in filenames like **Auto\ eth0**):

```

[802-3-ethernet]
mac-address=a4:ba:db:f8:d5:a1

[connection]
id=Auto eth0
uuid=e2bd6b42-0ae5-408e-aa12-c72cde0005d7
type=802-3-ethernet
**autoconnect=true**
timestamp=1293208113
```Then reboot and see if you have networking for netroot.

---

### Post by donniezazen on 2010-12-24
Thanks. It did not work. I was able to login by installing packages manually using live usb. The system was working just fine before the gdm problem but internet is not even working after logging in. Network applet says **No network devices available**

Thanks.

---

### Post by cariboo on 2010-12-24
Are you network devices detected? What's the ouput of:

```
sudo lshw -C network
```

If your wireless device is detected, but unclaimed, try the procedure [here]("http://ubuntuforums.org/showthread.php?t=571188")

---

### Post by ronacc on 2010-12-24
try disabling and re-enabling wireless I sometimes have to do that to get wireless to actually work under natty ( in my case it shows connected but isn't )

---

### Post by donniezazen on 2010-12-24
> **cariboo907 said:**
> Are you network devices detected? What's the ouput of:

```
sudo lshw -C network
```

If your wireless device is detected, but unclaimed, try the procedure [here]("http://ubuntuforums.org/showthread.php?t=571188")

Yeah, both wireless and Ethernet card are being detected. I am on my windows machine right now but i can get you the log if you want to take a look.

On netroot interface lshw -C network gave unclaimed. After logging in the devices were detected. I went to advanced drivers and network driver is not activated but i have been using this system with internet for as long as natty has been out.

Thanks.

---

### Post by donniezazen on 2010-12-24
> **ronacc said:**
> try disabling and re-enabling wireless I sometimes have to do that to get wireless to actually work under natty ( in my case it shows connected but isn't )

It didn't work man. Thanks.

---

### Post by cariboo on 2010-12-25
I managed to get an unclaimed wireless device working by using the following command:

```
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
```

---

### Post by donniezazen on 2010-12-31
Thanks i just reinstalled the newer image.

---

