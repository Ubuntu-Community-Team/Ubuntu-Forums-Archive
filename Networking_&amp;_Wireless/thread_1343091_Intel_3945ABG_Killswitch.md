---
title: "Intel 3945ABG Killswitch"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by nice_like_rice on 2009-12-01
Hi,

My wireless won't work, and through:

```
 dmesg | grep iwl3945 
```

I have determined the problem, as this returns

```
[  916.657752] iwl3945 0000:01:00.0: Radio disabled by HW RF Kill switch

```

The killswitch for the wireless is off. Pressing Fn+F2 is supposed to toggle the wireless, however when I do this, nothing happens and dmesg returns:

```
[ 1875.023932] atkbd.c: Unknown key pressed (translated set 2, code 0x84 on isa0060/serio0).
[ 1875.023935] atkbd.c: Use 'setkeycodes e004 <keycode>' to make it known.

```

I need some way of toggling this switch through ubuntu. I have tried resetting BIOS to default, I can't boot into windows to turn it on as I don't have windows.

I have tried

```
echo "0" >  /sys/bus/pci/drivers/iwl3945/0000\:01\:00.0/rfkill/rfkill0/state

```

but for some reason, it instantly resets itself to "2", and I can't figure out what is doing that (have even edited /usr/share/acpi-support/state-funcs, didn't help though).

I have tried

```
setkeycodes e004 x
```

up to 200, but still no success, very time consuming I will try 200+ later... (how many does it go up to?? 256?). Google can't find me a list of the various codes and their functions.

Any other suggestions, I'm getting desperate! Any ways I could stop the rfkill state reverting to "2"?

Thanks in advance,

david

---

### Post by nice_like_rice on 2009-12-01
Nobody?

---

