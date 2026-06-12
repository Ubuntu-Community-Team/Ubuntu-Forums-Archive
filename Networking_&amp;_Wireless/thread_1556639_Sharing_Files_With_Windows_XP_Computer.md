---
title: "Sharing Files With Windows XP Computer"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by GaryRixon on 2010-08-19
Hello, I am using ubuntu 10.04 desktop edition. I am using a wired connection to connect to my router. The windows xp pc is also using a wired connection. I enabled sharing of the folder which I would like to copy to my laptop (the ubuntu pc). When I click places>network>windows network it gives me an error message saying "failed to retrieve share list from server"

Any help or suggestions would be greatly appreciated, If you have any idea then please leave a comment.

Thanks in advance

---

### Post by jimbop99 on 2010-08-19
You have to install samba. Then open samba from administration menu. Select preferences>server settings. Make sure that the windows computer and the Ubuntu computer have the same network name.

---

### Post by GaryRixon on 2010-08-19
By network name do you mean the computer name ? I am a little confused at the moment.

---

### Post by jimbop99 on 2010-08-20
Under windows set up a home or small office netwok. The default name is set to "WORKGROUP". You can leave this as is or change it to whatever you like. Then in Ubuntu open samba and under preferences>server settings in the box that says Workgroup put in the same name as you did for the windows network. You'll need to reboot the windows machine and possibly the Ubuntu machine.

---

### Post by pricetech on 2010-08-20
Can you connect to the windows machine via IP ??  It may just be a browsing issue.

If you don't have a Samba entry under System - Administration then install system-config-samba in Synaptic.

---

