---
title: "Inherited Hardy Heron Domain controller and Windows Terminal Server"
date: 2013-03-13
forum: Networking &amp; Wireless
---

### Post by hankyknot on 2013-03-13
Hi folks,

I've just inherited a network that consists of a Hardy Heron Domain Controller and a Windows Server 2003R2 Terminal Server.

Everything seems to be working great apart from the fact that the Linux box is running out of space. As users are set up to use roaming profiles it can now no longer save roaming profiles due to lack of space. 

There is however lots of space on the Terminal Server so the Windows admin in me said why not just point their Terminal Services Profile to somewhere on the Terminal Server and then copy their Linux box profile over to that?

But alas this is Hardy Heron and I just don't know where the user profile mapping is set up and whether it even has an option for a Terminal Services profile.

Can anyone help?

My other option is to promote the terminal server to a DC and repurpose the linux box or lose it completely. While that may be an inevitable evolutionary step for the network I'm a little gun-shy of doing that right now.

---

