---
title: "FIX - Bluetooth - Broken on Resume  - 10.04 - Logitech DiNovo Desktop"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by slipdipper on 2010-10-07
If you're like me, you may have had to make some changes to your udev rules in order to get your precious Logitech DiNovo Edge working accordingly. (see [http://ubuntuforums.org/showthread.php?t=1528654](http://ubuntuforums.org/showthread.php?t=1528654)) 

Welp as you may have noticed, when your system returns from suspend mode, your mouse and keyboard may work, but the adapter is no longer in hci mode, but has reverted back to hid mode!

To fix:

Create a new script to make stuff work
```
sudo touch /etc/pm/sleep.d/10_bluetooth
```

become root, then fill it with goodies (have udev re-eval stuff):
```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    thaw|resume)
    udevadm trigger
    ;;
    *)
    ;;
esac

```

Set it to be executable
```
sudo chmod +x /etc/pm/sleep.d/10_bluetooth
```

And then put your system to sleep and bring it back to life to test!

---

### Post by randyr505 on 2011-01-21
Thanks! This worked great for me. I am running 10.04 with a Dell bluetooth keyboard and mouse.

> **slipdipper said:**
> If you're like me, you may have had to make some changes to your udev rules in order to get your precious Logitech DiNovo Edge working accordingly. (see [http://ubuntuforums.org/showthread.php?t=1528654](http://ubuntuforums.org/showthread.php?t=1528654)) 

Welp as you may have noticed, when your system returns from suspend mode, your mouse and keyboard may work, but the adapter is no longer in hci mode, but has reverted back to hid mode!

To fix:

Create a new script to make stuff work
```
sudo touch /etc/pm/sleep.d/10_bluetooth
```

become root, then fill it with goodies (have udev re-eval stuff):
```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    thaw|resume)
    udevadm trigger
    ;;
    *)
    ;;
esac

```

Set it to be executable
```
sudo chmod +x /etc/pm/sleep.d/10_bluetooth
```

And then put your system to sleep and bring it back to life to test!

---

