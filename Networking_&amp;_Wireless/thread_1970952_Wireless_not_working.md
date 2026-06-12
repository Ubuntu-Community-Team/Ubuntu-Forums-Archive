---
title: "Wireless not working"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by alexjpowell on 2012-05-01
My laptop is a Dell Studio 17
I've tried a few different things on here but alas, no luck
I recently upgraded to 12.04 and it just stopped working. I click the network icon in the top right and nothing wireless comes up. It's not a listed driver either and installing firmware-b43-installer didn't do anything.

It was working for a while after the upgrade by simply using an earlier kernel but since installing updates today it has stopped working on that as well.

---

### Post by alexjpowell on 2012-05-02
OK well I pressed the toggle wireless button and wireless became "activated" but said that no driver was installed. I went into additional drivers and installed the driver and rebooted. But, as the law of the sod would have it - no wireless still, although the driver is installed, activated but "currently not in use"

---

### Post by alexjpowell on 2012-05-02
just typed
sudo modprobe wl
and it started working
I literally have no idea

---

