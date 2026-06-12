---
title: "Samba - Mask Questions."
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by Roasted on 2010-05-18
In the samba config file, there's two general entries for create mask and directory mask that are commented out with a ;. Of course you can take that out and edit the masks accordingly to what you want.

Question is this. If I want ALL of my shares to be 775, but I want one particular share to be 644, can I simply set 775 to the directory mask + create mask and then add individual lines on the odd-ball share to force ONLY that share to have 644 masks? 

I'd try it if I were on an Ubuntu computer, but I won't be at one for another 1-2 days.

---

### Post by bab1 on 2010-05-18
> **Roasted said:**
> In the samba config file, there's two general entries for create mask and directory mask that are commented out with a ;. Of course you can take that out and edit the masks accordingly to what you want.

Question is this. If I want ALL of my shares to be 775, but I want one particular share to be 644, can I simply set 775 to the directory mask + create mask and then add individual lines on the odd-ball share to force ONLY that share to have 644 masks? 

I'd try it if I were on an Ubuntu computer, but I won't be at one for another 1-2 days.

All is revealed under the heading "Interaction with the Standard Samba “create mask” Parameters" located: [**_here_**]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2614099").

If your direct question is: Can I add *create mode *parameters in the individual share?  The answer is yes.

---

### Post by Roasted on 2010-05-19
> **bab1 said:**
> All is revealed under the heading "Interaction with the Standard Samba “create mask” Parameters" located: [**_here_**]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2614099").

If your direct question is: Can I add *create mode *parameters in the individual share?  The answer is yes.

I just wanted to make sure that the individual modes on the individual shares would override the global setting I have set further up for all shares.

---

