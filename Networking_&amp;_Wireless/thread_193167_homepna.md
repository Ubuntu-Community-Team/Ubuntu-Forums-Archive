---
title: "homepna"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by escifell on 2006-06-09
I have just upgraded to dapper from breezy and my AMD79c978[HomePNA] has ceased to connect to my network.

In Breezy I had the line 'pcnet32 homepna=1' in my /etc/modules file to force the driver to use PNA mode rather than the default ethernet mode. What is the magic line for Dapper please, as this clearly no longer works?

Thanks

---

### Post by ns2048 on 2006-06-10
Try adding the following line to '/etc/modprobe.d/options'

options pcnet32 homepna=1

Does that work?
--ns2048

---

### Post by escifell on 2006-06-12
That is a part solution. Having dug around a bit more it is tha same problem as Breezy. Namely the pcnet32 driver is preloaded into the kernel to use ethernet so the module-init-tool called during boot that reads the /etc/modules file does nothing to the pcnet32 configuration. The complete solution is:

1) add line in module-tools-init to unload the pcnet32 driver from the kernel prior to reading the modules file

# Loop over every line in /etc/modules.
[COLOR="Red"]modprobe -r pcnet32 > /dev/null  2>&1[/COLOR]
log_begin_msg 'Loading modules...'
grep '^[^#]' $MODULES_FILE | \
while read module args; do
  [ "$module" ] || continue
  if [ "$VERBOSE" != no ]; then
    log_begin_msg "Trying module $module"
    if modprobe $module $args >/dev/null 2>&1; then
      log_end_msg 0
    else
      log_end_msg 1 || true
    fi
  else
    modprobe $module $args >/dev/null 2>&1 || true
  fi
done
log_end_msg 0

2) add line to /etc/modules
[COLOR="Red"]pcnet32 homepna=1[/COLOR]

3) reboot

---

### Post by hafuch on 2006-06-16
Hi All (and especially us newbies),

If you're having trouble locating the file to modify, open the teminal (under Applications/Accessories menu) and type (or copy/paste) the following command :

sudo gedit /etc/init.d/module-init-tools

Then follow escifell's instructions in Steps 1, 2, and 3.

It works PERFECTLY for this AMD 79C978 homepna card.

Good luck, and thanks to escifell and others for their contributions!

Hafuch

---

### Post by koki on 2006-12-30
> **escifell said:**
> 1) add line in module-tools-init to unload the pcnet32 driver from the kernel prior to reading the modules file

# Loop over every line in /etc/modules.
[COLOR="Red"]modprobe -r pcnet32 > /dev/null  2>&1[/COLOR]

2) add line to /etc/modules
[COLOR="Red"]pcnet32 homepna=1[/COLOR]

3) reboot

This worked great! Thanks!

---

