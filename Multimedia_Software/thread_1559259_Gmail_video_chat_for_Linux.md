---
title: "Gmail video chat for Linux"
date: 2010-08-23
forum: Multimedia Software
---

### Post by mhenriday on 2010-08-23
Ever since the first version for Windows was released in 2008, lots of us **Gmail** users have been nagging the developers to release a plugin that worked with **Linux**. A few days ago, our prayers and petitions were finally answered : **Google** released a [**Debian** plugin]("http://gmailblog.blogspot.com/2010/08/use-linux-now-you-can-video-chat-too.html"). I immediately installed it on my main stationary box and on my main laptop, both of which are running 64-bit **Lucid**, but with very different results - on the former the plugin is recognised by the machine and when I click on the little web cam icon when starting a chat, video starts, on the latter, however, I get a link which suggests that I _add_ the plugin ! Checking on Synaptic, I find that version 1.4.1.0-1 of «google-talkplugin» has been installed on both boxes ; moreover, «/opt/google/talkplugin» contains precisely the same folders and files. But when I check my plugins from the «about:plugins» button on my **FF** browser (the same version (**Mozilla/5.0 (X11; U; Linux x86_64; sv-SE; rv:1.9.2.9pre) Gecko/20100822 Ubuntu/10.04 (lucid) Namoroka/3.6.9pre GTB7.1**) on both machines), I find to my surprise that the> Google Talk Plugin Video Accelerator

    Filename libnpgtpo3dautoplugin.so
    Plugin Version: 
    Plugin Description: Google Talk Plugin Video Accelerator version:0.1.43.3

mimetype     Description     Extensions     Enabled
application/vnd.gtpo3d.auto     O3D MIME         Yesand the> Google Talk Plugin

    Filename libnpgoogletalk64.so
    Plugin Version: 
    Plugin Description: Version: 1.4.1.0

mimetype 	Description 	Extensions 	Enabled
application/googletalk 	Google Talk Plugin 	googletalk 	Yesfiles, which are listed in the case of the stationary box, are absent in the case of the laptop. *Das also war des Pudels Kern !* I've tried deleting the plugin package and re-installing it several times, but no joy. And, as Mr Murphy's law would demand, the irony of the matter is that I don't have a web camera installed on the stationary box and the microphone plug is dodgy, so I can't even run ordinary sound chat from a headset there, while both function splendidly on the laptop ; thus, e g, **Skype for Linux** works fine....

Any suggestions as to what can have gone wrong with the installation process on the laptop and how I can correct it ? Any help that can be provided will be most appreciated !...

---

