---
title: "How to assign static ip"
date: 2012-07-02
forum: Networking &amp; Wireless
---

### Post by Rktech on 2012-07-02
Hi,
I am using Ubuntu server 11.04, I would like to change DHCP to static IP. I tried through vi /etc/network/interfaces but it unable to save for some reason, is it any other way to change it. I am new to Linux, Please help me with all option.
Thanks
RK

---

### Post by Cheesehead on 2012-07-02
> **Rktech said:**
> vi /etc/network/interfaces
Editing that file requires sudo. Without sudo, it will open read-only.
[FONT="Courier New"]sudo vi /etc/network/interfaces[/FONT]

---

### Post by Rktech on 2012-07-02
> **Cheesehead said:**
> Editing that file requires sudo. Without sudo, it will open read-only.
[FONT="Courier New"]sudo vi /etc/network/interfaces[/FONT]

I tried now and trying to saving with :w but it can't and says you can't edit read only file.

---

### Post by sudodus on 2012-07-02
> **Cheesehead said:**
> Editing that file requires sudo. Without sudo, it will open read-only.
[FONT="Courier New"]sudo vi /etc/network/interfaces[/FONT]
+1

At least in my system the file has write permission for root alias superuser. Add sudo in front of your command line, and it should be possible to write to the file.

---

### Post by papibe on 2012-07-02
Hi Rktech.

Another option is to set an reservation on your router.

Just a thought.
Regards.

---

### Post by Cheesehead on 2012-07-03
> **Rktech said:**
> I tried now and trying to saving with :w but it can't and says you can't edit read only file.

Try it again. If you really used sudo, then the file is not read-only.

---

