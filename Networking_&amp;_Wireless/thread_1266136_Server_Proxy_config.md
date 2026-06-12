---
title: "Server Proxy config"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by dimothy10 on 2009-09-14
Am having a bit of difficulty with my Ubuntu server installation.  I am running 9.04 Server as a VM at work here so I can install Joomla and have a play with it basically.  

I have installed it as a LAMP server with OpenSSH.

During the install process I entered what I believed to be the correct proxy settings but upon getting in to Ubuntu I think I may have errored slightly.  Where is the information for connection through a proxy server stored in Ubuntu?  Or is it a requirement to configure each individual application with its own proxy settings?  The application I was most hoping to use was to wget (so I can install the latest version of Joomla direct form source).

In the native windows domain environment I understand how to set the proxy for the various browsers.  My other query would then be how to configure authentication to use the proxy in my VM?  On the host machine I am assuming it picks up my domain authentication from AD and uses that.  Is there a way to pass this though to the Guest OS or will I need to ask one of our server admins to create another account?

Cheers

Tim

---

### Post by dimothy10 on 2009-09-14
Ok, so have been doing some more reading and looking at our network setup.  From what I can ghather the proxy is windows based (blue coat proxy) and from what I understand apt and wget do not allow authentication (NTLM)?  Is this correct or have I got the wrong end of the stick?

Cheers

Tim

---

