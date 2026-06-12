---
title: "having problem adding hidden wireless network"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by unix1adm on 2011-05-31
I have a hidden wireless network. 

I know the ssid is SOMENETWORK
auth/encrypt is WPA2 with AES
I know the Preshare Key is....xxxxx
Its a manual IP addr assignment not dhcp. 
and I know the DNS address


I try to connect to it and it fails so i went to the menu/system/prefrences/network connections.

I am logged in as my self not root. 

It opend the pannels and I select wireless tab/add
I get the next pannel and type ins SOMENETWORK for my connection name. 

In the IPv4 setting I say manual ip not DHCP But the apply button is grayed out. None of the changes I do will work. 

Normaly it askes me for my password to make the changes. In this case it is not asking me. 

What am I missing here? 

Thanx

---

### Post by walt.smith1960 on 2011-05-31
When you are logged onto an account with administrative privileges, go to Users and Groups -> advanced settings.  Make sure your user account can use connect to networks.  It seems silly to me that "Connect to the Internet using a modem" is selected by default but "Connect to wireless and ethernet networks" is not.  I'm pretty sure that you have to have the wireless and ethernet networks box checked in order to manually configure a network as a desktop user.

---

### Post by unix1adm on 2011-05-31
> **walt.smith1960 said:**
> When you are logged onto an account with administrative privileges, go to Users and Groups -> advanced settings.  Make sure your user account can use connect to networks.  It seems silly to me that "Connect to the Internet using a modem" is selected by default but "Connect to wireless and ethernet networks" is not.  I'm pretty sure that you have to have the wireless and ethernet networks box checked in order to manually configure a network as a desktop user.

yes my ID has these permissions. I have done this before a while ago. So maybe something got broken on an update?

---

