---
title: "how to restart x11vnc"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by mahmoodn on 2010-09-13
How can I restart x11vnc service?

---

### Post by Threk on 2011-04-20
I have the same question. I can ssh in fine, but x11vnc has crashed and I need to see the result that should be visible on the desktop. (Laptop with a fried screen) Rebooting will get x11vnc running again but then I need to start over.

When it crashes how do you restart it?

---

### Post by krunge on 2011-04-20
> **Threk said:**
> I have the same question. I can ssh in fine, but x11vnc has crashed and I need to see the result that should be visible on the desktop. (Laptop with a fried screen) Rebooting will get x11vnc running again but then I need to start over.

When it crashes how do you restart it?
Is there an X server running?  Is it your X session or is it at the login panel? "ps wwaux" may answer these questions for you.

```
x11vnc -display :0
```
will probably get you started, but since I don't know the answer to my above question there may be other options you need to specify (or run as root if the X server is still at the login panel.)

---

### Post by HallCrash on 2012-06-01
I was able to obtain the PID of x11vnc by using ```
pgrep x11vnc
```

Then I was able to kill the process using ```
sudo kill ####
```

I was unable to restart x11vnc I got an error that had to do with UltraVNC file transfer

```
tail: cannot watch `/tmp/x11vnc.tray.djeZ8l': No such file or directory
tail: cannot watch `/tmp/x11vnc.tray.djeZ8l': No such file or directory
    while executing
"close $channel"
    (procedure "read_client_info" line 25)
    invoked from within
"read_client_info $client_tail"
    (procedure "read_client_tail" line 5)
    invoked from within
"read_client_tail"
```

hope that helps.

---

