---
title: "&quot;Mounting&quot;Mp3 devices on Feisty"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by ratbagradio on 2007-04-23
I'm on Feisty after been almost 4 weeks on Ubuntu (Linux first-timer).

I use Amarok and its a great player -- the best I've ever found. But while I Ubuntu recognizes my iRiver T30 I cannot follow the directions as to how to link that up for syncing with Amarok.

The Amarok wiki says this:

> Add the following lines to a file under your udev rules directory, preferrable is to create a new file for it (eg /etc/udev/rules.d/libmtp.rules) or just to copy libmtp.rules file (the one you get when you compile libmtp) under that directory....
# iRiver T30
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1119", SYMLINK+="libmtp-%k", MODE="666"

and I have no idea whatsoever what that means. On my iRiver the "Mount" is referred to in the "properties" but I'm unsure how to employ that too as even though I import that into the configure setting it isn't enough or is wrong. I also am confused over what is and isn't MTP(& MTP don';t require a "mount" reference?)

I can transfer Mp3 files to my iRiver easily so long as I don't try to sync them via Amarok as I haven't been able to configue the connection.

---

