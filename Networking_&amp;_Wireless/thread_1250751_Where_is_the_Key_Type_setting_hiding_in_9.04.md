---
title: "Where is the Key Type setting hiding in 9.04?"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by ret3 on 2009-08-26
I'm trying to connect to my school's wireless network, but the instructions ( [https://management.pna.utexas.edu/static/faqs/dot1x/dot1x-linux.html](https://management.pna.utexas.edu/static/faqs/dot1x/dot1x-linux.html) ) reference an older version of the Network Manager. In particular, I need to know how to set the **Key Type** and what to do with the **Anonymous Identity** and **Inner Authentication** that the configuration dialogue now has. How do these instructions translate into Jaunty-ese? 

   > 1. Download the certificate file. You can obtain this file from the guest.utexas.edu wireless network if necessary.
   2. Click the Network Manager icon and select the restricted.utexas.edu wireless network.
   3. Select the following options in the Wireless Network Key Required dialog box.
          * Wireless Security: WPA2 Enterprise [recommended] or WPA Enterprise.
          * EAP Method: TTLS
          * Key Type: AES [recommended for WPA2] or TKIP
          * Password: [Your UT EID password]
          * CA Certificate File: cacerts.pem

      Keep the default settings for the other fields in the dialog box.

      Note: The WPA2 security protocol is recommended for campus wireless network users; however, the network also supports WPA. Select the AES encryption type for WPA2 and the TKIP type for WPA.
   4. Click the Connect button to complete the configuration and connect to the restricted.utexas.edu network.


---

