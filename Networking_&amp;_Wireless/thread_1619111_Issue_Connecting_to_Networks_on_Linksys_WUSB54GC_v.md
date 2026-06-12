---
title: "Issue Connecting to Networks on Linksys WUSB54GC v3"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by MrMatt2532 on 2010-11-11
I just did a clean install of ubuntu 10.10 on one of my older desktops without wireless. I then inserted the linksys WUSB54GC v3 to try to connect to the internet.

It appears the device is working well as it is instantly recognized by the pc with no configuration necessary and it can see several wireless networks.

Now when i try to connect to the networks, it just tries and tries without ever connecting and eventually gives up.

Any ideas for what to try?

Thanks.

---

### Post by CTBuckweed on 2010-11-11
> **MrMatt2532 said:**
> I just did a clean install of ubuntu 10.10 on one of my older desktops without wireless. I then inserted the linksys WUSB54GC v3 to try to connect to the internet.

It appears the device is working well as it is instantly recognized by the pc with no configuration necessary and it can see several wireless networks.

Now when i try to connect to the networks, it just tries and tries without ever connecting and eventually gives up.

Any ideas for what to try?

Thanks.

We need more information....

Has the network adapter (USB I guess) worked before on another system? to the very same router that you have? Offhand, check your router for MAC filtering for wireless connections and check your WPA/WEP settings. They have to have the same key.

---

### Post by MrMatt2532 on 2010-11-11
> **CTBuckweed said:**
> We need more information....

Has the network adapter (USB I guess) worked before on another system? to the very same router that you have? Offhand, check your router for MAC filtering for wireless connections and check your WPA/WEP settings. They have to have the same key.

This is a new USB adapter, so I have never had it working yet.

The network i'm trying to connect to is the type that looks open and then, when you connect to it and try to navigate to a page, it redirects you and asks for your logon credentials.

---

### Post by uncaspi on 2010-11-11
I understand you are trying to connecct to an open network whitout a key? Are you redirected to the login page or will it just not connect at all?

---

### Post by CTBuckweed on 2010-11-11
> **MrMatt2532 said:**
> This is a new USB adapter, so I have never had it working yet.

The network i'm trying to connect to is the type that looks open and then, when you connect to it and try to navigate to a page, it redirects you and asks for your logon credentials.

Well, if web pages appear that ask for logon credentials, then the adapter is working with ubuntu. I appears the whatever you are connecting to requires that you have an ID/password. The adapter works...

---

