---
title: "Terminal Server w/ WHS console help"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by racecarpete on 2009-05-25
Hey guys, so I'm trying to access my Windows Home Server console from my desktop running Ubuntu 9.04. 

There was a recent post on the microsoft WHS blog on how to do this with a MAC. Here is the link.

[Access WHS console through Remote Desktop on a MAC]("http://blogs.technet.com/homeserver/archive/2009/04/29/running-the-windows-home-server-console-on-a-mac.aspx")

I'm trying to adapt the above instructions to work with Ubuntu. I can create a RDP connection to my server no problem. The issue I am having is when I try to get the console to launch as in step 7.

> 7. In the Applications tab, make sure Start only the following Windows-based application when you log in to the remote computer is checked and type the following for Application path and file name: C:\Program Files\Windows Home Server\HomeServerConsole.exe /b

So under the "Programs" tab, I copy the application path and click the "Start the following program on Connection" box. 

Now, when I try to connect, I get an error from WHS saying, "The terminal server has exceeded the maximum allowed connections." If I disable the "Start the following program on Connection" box, the RDP will launch to the desktop without issue.

I'm also not quite sure what the /b switch is supposed to do. I tried removing that and I get the same error.

Can anyone help me out ? 

Thanks,
Peter

---

### Post by racecarpete on 2009-05-25
Ok, so I got this to work. I found a list of settings that need to be made for RDP and copied them in and it now works.

Here is a link to the settings. 

[WHS Console Settings]("http://wiki.wegotserved.com/index.php?title=Create_a_Desktop_WHS_Console_Link")

However, I now have two problems. 

1.) The window is cut off. It seems to cut off the last 1/5th of the console. I'm not quite sure what adjusts this. I tried adjusting the desktopwidth but that does not seem to have any effect.

2.) I saved the config onto my desktop. So I have file named "WHS Console.rdp" Is there a way to make this automatically open terminal services? Right now I have to open terminal services and then open these settings.

Thanks,
Peter

---

### Post by racecarpete on 2009-05-26
So I have narrowed down the problem to the "winposstr" setting. This is supposed to handle how windows are launched on the remote server. However, no matter what i set this to, the settings do not change.

I have a feeling that this might be a bug in the ubuntu terminal server client. Can anyone comment on this?

---

