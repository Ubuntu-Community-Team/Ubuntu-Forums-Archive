---
title: "Toshiba Satellite 4600 wireless PCI hell"
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by dickmorrell on 2006-07-01
After using Hoary and Breezy with instant detection of the onboard Lucent mini PCI card I then install Dapper on the laptop. Dapper doesn't see the onboard Lucent card at all although the kernel does and I can see it in output as below say by typing sudo lshw -C network

  *-network
       description: Wireless LAN Card
       product: Version 01.01
       vendor: TOSHIBA
       physical id: 0
       slot: Socket 0

If I try and identify it further:

# sudo cardctl ident

Socket 0:
  product info: "TOSHIBA", "Wireless LAN Card", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)

But nothing, hence to say concerned why Dapper is causing so many people to have previously happy working wireless and now busted. Also remember the Lucent Orinocco is one of the OLDEST supported chipsets that Linux has supported and a staple fair of Linux users.

Soooo... you'd expect it to work.

Any hints tips appreciated.

Dick

---

