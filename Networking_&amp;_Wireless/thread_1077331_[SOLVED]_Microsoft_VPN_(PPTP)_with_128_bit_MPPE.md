---
title: "[SOLVED] Microsoft VPN (PPTP) with 128 bit MPPE"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by stuples on 2009-02-22
Hi

Firstly, this is my first proper post.

I've not been able to use VPN for a long while now despite trying all the different solution guides that are on here.

I needed 128 bit encryption but if you set this in the Advanced Settings it automatically gets reset. I got round this by setting it using the gconf-editor:

Begin by opening a terminal and typing:
```
gconf-editor
```

Then on the left pick:

system -> networking -> connections -> 1 (some number) -> vpn

On the right will be a list of keys. Right click in there and create a new key with the name:
```
require-mppe-128
```

The type is string, with the value:
```
yes
```

Close the editor and try out your connection.

I also don't use the domain field in the settings. I just include the domain name in the user field: DOMAIN\user.

Hope this helps.

---

