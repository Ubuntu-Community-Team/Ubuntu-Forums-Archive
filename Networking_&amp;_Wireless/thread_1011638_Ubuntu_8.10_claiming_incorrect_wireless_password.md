---
title: "Ubuntu 8.10 claiming incorrect wireless password"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by TJTorola on 2008-12-15
Hi all, I just installed 8.10 very recently on my inspiron 1525. It all went smoothly until I got to wireless. I was able to find the connection no problem but when I enter the password it doesn't accept it. It just keeps asking me for it. Its a WPA & WPA2 increpted password. I know its the correct one as I can still connect on another laptop with windows. Any ideas would be greatly appriciated. Thank you much for any help you can give.

---

### Post by frankleeee on 2008-12-15
Try checking the right click on the bars edit-wireless and see if your password is correct, you can click on see the password. So are you having problems with the key or the wireless, in intrepid you can set a key or leave it blank hit accept and autologin if your wpa is correctly set up in the edit wireless.

---

### Post by sampmoody on 2008-12-15
Hello,

I have the exact same problem using Acer Aspire 2920. I can see the network but when the key is entered it fails to connect. Then after failing to connect if I view the key it has been correupted. i.e. the characters are changed and the key is twice the length of the one I entered. The wireless was working fine for 8.04 and is still fine when booting to windows. Any ideas much appreciated.

---

### Post by frankleeee on 2008-12-15
> **sampmoody said:**
> Hello,

I have the exact same problem using Acer Aspire 2920. I can see the network but when the key is entered it fails to connect. Then after failing to connect if I view the key it has been correupted. i.e. the characters are changed and the key is twice the length of the one I entered. The wireless was working fine for 8.04 and is still fine when booting to windows. Any ideas much appreciated.

In my experience doing a edit wireless with a right click fixes this problem you re-enter the correct password in the edit, which can be done while the gui is still up refusing the correct one. You can also reset the key to access by going to gnome2 in home and putting the key in the trash, then either setting the key for access when the new key request appears or leave it blank hit accept and you will auto enable the wireless if you have checked the edit wireless when refused. Once you set the wireless password in the edit it will stay the same.

---

### Post by sampmoody on 2008-12-15
> **frankleeee said:**
> In my experience doing a edit wireless with a right click fixes this problem you re-enter the correct password in the edit, which can be done while the gui is still up refusing the correct one. You can also reset the key to access by going to gnome2 in home and putting the key in the trash, then either setting the key for access when the new key request appears or leave it blank hit accept and you will auto enable the wireless if you have checked the edit wireless when refused. Once you set the wireless password in the edit it will stay the same.

I tried both these suggestions but no success. If I delete the key in .gnome2/keyrings then as you say I am prompted to set the key. The file default.keyring is created and on inspection contains the correct key. Using the right click edit also shows the correct key. When I try to reconnect the connection fails and the key is again wrong in the GUI. I therefore have rechecked the default.keyring file and can see that the key is now corrupted here too! Any other suggestions?

---

