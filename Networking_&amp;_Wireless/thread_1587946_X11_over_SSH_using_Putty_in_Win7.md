---
title: "X11 over SSH using Putty in Win7"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by coolrazor on 2010-10-04
I've read a number of web pages on this and scoured a few forums, but I can't seem to get it to work.  Here's the low down so far:

[don't know if this matters] server has a bridge interface

Edited /etc/ssh/sshd_config
  X11Forwarding yes
  X11DisplayOffset 10

Edited /etc/ssh/ssh_config
Host *
    ForwardAgent yes
    ForwardX11 yes
    ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes

Putty: X11 page
  checked the "enable X11 forwarding" checkbox
  X Display Location: localhost:0

Checked /etc/hosts file and it has "127.0.0.1 localhost" (some other people had a problem with this)

When I log in via Putty, as the user I'll try xterm and get:
  tim@matrixreloaded:~$ xterm
  xterm Xt error: Can't open display: localhost:10.0

If I sudo to root and try it I get:
  root@matrixreloaded:/home/tim# xterm
PuTTY X11 proxy: wrong authentication protocol attemptedWarning: This program is an suid-root program or is being run by the root user.
The full text of the error or warning message cannot be safely formatted
in this environment. You may get a more descriptive message by running the
program as a non-root user or by removing the suid bit on the executable.
xterm Xt error: Can't open display: %s

Any ideas on what to do?  Brand new server install too.  :???:

---

### Post by SeijiSensei on 2010-10-04
Windows 7 doesn't know anything about X-Windows.  I believe there are some X-Windows implementations for Windows, but having never used them, I can't give you any help in that regard.  This page looks promising, though: [http://128.100.5.70/wiki/RemoteAccess/SSHTunneling/XWindowsWindows](http://128.100.5.70/wiki/RemoteAccess/SSHTunneling/XWindowsWindows)

---

### Post by coolrazor on 2010-10-05
yeah, that didn't help me.  I've tried the putty instructions and I would really rather not use cygwin on this computer.

---

### Post by anglican on 2010-10-05
> **coolrazor said:**
> yeah, that didn't help me.  I've tried the putty instructions and I would really rather not use cygwin on this computer.Then follow the advice on that page and google "Windows X servers". Xming works well - top of the list when I googled.

H

---

### Post by coolrazor on 2010-10-05
Tried Xming and it looks like it is working pretty well.
Still wondering if it is possible without Xming, but this works for my purposes.

---

### Post by joberly on 2010-10-05
Nope, not possible. Windows does not know how to render applications in the Linux world, so you need a 3rd party Xwindows renderer.

---

