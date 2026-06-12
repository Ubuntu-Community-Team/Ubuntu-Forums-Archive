---
title: "Internet doesnt work after reboot in my Ubuntu 12.04"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by msankar on 2012-05-27
Hi team
I am having a weird problem. Let me explain in detail about it. 

a. My INTERNET works perfectly fine. But...
b. But after reboot it just stops working. Dont know why. Then I follow the work around which would bring me scenario a)

My work around is as follows:
1. cd /etc/network
2. sudo vi interfaces

3. Add the following lines of code
auto eth0
iface eth0 inet dhcp

4. Reboot

5. Internet works.  But can not connect to my company VPN account. :(

6. So i remove the lines I have added in step3. And reboot

7. Now everything works fine as brand new. NO issues till reboot again.

Can you please help what could be the reason for this strange behavior?

I have a broadband connection - Ethernet (wired) type connected to my BELKIN ROUTER.

Please help in this regard. Appreciate any kind of help.:)

Thanks
Sankar Malladi

---

### Post by nothingspecial on 2012-05-29
*Thread moved to **Networking & Wireless**.*

---

