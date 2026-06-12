---
title: "Getting minimal install to  use /etc/hosts"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by Xyem on 2009-02-25
I'm trying to do a minimal install inside a virtual machine ( qemu ) but I've come across a couple of issues.

Firstly, and every issue hereafter stems from this, is even though I select the host ( 10.0.2.2 ) as the mirror because I have an apt-mirror of the ubuntu repositories, the installer still tries to access security.ubuntu.com even though my mirror mirrors that too. This would be fine if I had a direct connection to the internet but I don't. The first issue it causes is the installer will freeze for close to half an hour ( as the wget's etc. time out ).

As a fix, I thought I would just add, in the guest, this to /etc/hosts during the installation:
> 10.0.2.2 security.ubuntu.com
so that the requests would be redirected to the host and accessed from the mirror. As you've probably guessed, it doesn't work.

This lead me on a wild goose chase involving nsswitch.conf, resolv.conf, host.conf ( which doesn't exist in the installer ) and nothing I tried worked. It either tries to use DNS and fails or I get 'bad address', even for localhost. I simply can't get 'security.ubuntu.com' to resolve to '10.0.2.2'

More annoying perhaps, is that it works fine on the host which was installed from the very same CD.

Can anyone steer me in the right direction? Please?

---

