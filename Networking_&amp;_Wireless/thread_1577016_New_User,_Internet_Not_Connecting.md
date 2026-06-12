---
title: "New User, Internet Not Connecting"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by noren on 2010-09-18
Hi there,

I have been using ubuntu for past many years, but always been as a single user on my laptop or desktop.

Now i wanted to create a new login for my sister, but i am unable to configure wifi-internet connection for the new user.

My login is also in sudoers list, but i have not kept the new loging in the sudo list. I can access internet through my login but cant do the same with my sisters login.

My loging is able to launch and connect via nm-applet, but nm-applet is not even opening in the sisters' login. its giving me some D-Bus error.

Advice needed here

Please help

Noren

---

### Post by grahammechanical on 2010-09-18
As you installed Ubuntu on the machine and put in a password for yourself, you are classed as the administrator. You should have all the privileges of the administrator. Any other user will have a limited set of privileges defined by you. You may not have given your sister access to the wireless network. There are two ways to do this: a secure way or an unsecure way.

1) Right click the network manager icon. Select Edit Connections. Select Wireless. Select your wireless connection. Click Edit. Enter your login password and check (tick) Available to all Users. Make sure Connect Automatically is checked also.

2) System >Administration >Users and Groups. Select your sister's User account. Select Advance Settings. Enter your login password. Go through the list of privileges. Look for Connect to internet Using Modem, Connect to wireless and ethernet networks, Use modems. 

Regards.

---

