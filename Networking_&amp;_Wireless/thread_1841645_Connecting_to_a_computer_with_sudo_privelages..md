---
title: "Connecting to a computer with sudo privelages."
date: 2011-09-09
forum: Networking &amp; Wireless
---

### Post by ironic.demise on 2011-09-09
Here's the scenario.
Laptop, Desktop.
Each runs Ubuntu 11.04 i386.
Desktop (Server) has Apache2 installed, and working... I'm fairly aware of apache and how to use it, as far as I can tell.

How do I log in on the laptop and change /var/www

WITHOUT setting /var/www as rwx for everybody and sharing it and WITHOUT using ubuntuone?

Things I'm trying to do, Log in via terminal as desktopuser@desktopserver or locallaptopuser@desktopserver with permissions set to allow sudo privelages to the laptop users and obviously desktop too, and nobody else.

ssh right?

ssh is giving me port 22 refused, I've disabled all firewalls to test this.

Nevermindums. solved.

Had to install ssh on both machines.

---

