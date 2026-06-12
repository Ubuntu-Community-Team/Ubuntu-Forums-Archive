---
title: "cell phone + bluetooth connection confuses me."
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by nightrider.36 on 2009-03-31
Greetings all, I'm using 9.04 now and seems to be working fine. I thought 9.04 would fix the my bluetooth + cell phone connection problem but it is not to be.  I don't think the problem is with my phone because Windows bt apps connect to the phone perfectly so it has to be (clutch the pearls) the Gnome BT applet. On Ubuntu, I'm using the Gnome Bluetooth Applet 1.8. BT is not built in to the laptop, it's running from a USB port as a plug-in hardware.

**the problem:**
[LIST]
[*]My cellphone's bt applet doesn't recognize gnome bt applet.
[*]the Gnome bt applet finds my phone and pairs succesfully.
[*]I can browse the phone's folders and transfer a few files but the drops the connection. I have to delete the connection and completely re-pair. In fact, sometimes I have to re-start Ubuntu completely. Sometimes that doesn't help either.
[/LIST]

**Error messsage:**
I get this message after the applet drops the connection.
> The Folder contents could not be displayed.

Method "GetCurrentPath" with signature "" on interface "org.openobex.session" doesn't exist.

I'd like to be able to "send" files to the GNOME BT Applet like I do on using the applet that installs on Windows. I don't know enough about troubleshooting BT connection problems to diagnose this issue. Could it be that it's running from the USB port? I don't know. Any help would be appreciated.

Thank you.

---

### Post by faster1982 on 2009-05-27
I'm also getting this message. I was able to browse file once using bluz obex utils.

Using Ubuntu 9.04.

---

### Post by sanderj on 2009-07-26
I've got the same problem on my Fujitsu Siemens Lifebook E8110 with Centrino Duo chipset, trying to connect to my Nokia N95 8GB.

And *if* the connections succeeds, copying more than 3 files of 0.8 MB each, (almost?) always results in a dropped connection.


Error message:

```
Could not display "obex://[00:1F:00:B0:00:34]/E:/Images".

Error: Method "GetCurrentPath" with signature "" on interface "org.openobex.Session" doesn't exist

Please select another viewer and try again.
```


With a 2.50 US$ USB stick, I haven't seen the problems so far.

---

### Post by exutable on 2009-09-11
I have the same exact problem

```
Method "GetCurrentPath" with signature "" on interface "org.openobex.Session" doesn't exist
```

---

### Post by dzon65 on 2009-09-11
The standard installed bluetooth confused me as well.In order to get this working,I installed "share files with bluetooth".Applications,install (just type bluetooth,it'll pop up).
Now,whether it's sending to device (mobile or example) or receiving from,it's done with a simple click on the new bluetooth icon.Be sure your device is set up.

---

