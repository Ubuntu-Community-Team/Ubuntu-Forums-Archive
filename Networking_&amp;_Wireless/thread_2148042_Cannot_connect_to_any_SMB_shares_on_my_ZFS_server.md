---
title: "Cannot connect to any SMB shares on my ZFS server"
date: 2013-05-23
forum: Networking &amp; Wireless
---

### Post by NOTORIOUS VR on 2013-05-23
I've tried a few different flavors of Ubuntu recently, Ubuntu Gnome, Linux mint, etc.. 

All of which I cannot seem to be able to connect to any of my shares on my ZFS file server (it's running OpenSolaris).  I can connect to my windows box if I create a share strangely enough.

I'm not sure what the issue is, my Ubuntu server box can connect just fine and can any of my Android tablets, and windows boxes.

Heck I cannot even connect to my public/guest=on shares that don't require any form of authentication.  Ubuntu's file managers just keep asking for a login to see/access the share and every time I enter the info, the login box just pops right back up.

Does anyone know why this would be happening?  All the installs are just pure/fresh installs. No extra software is installed.  I've read of some issues with smb.conf causing this, but I don't see why there would be any issues to begin with.

---

### Post by 2F4U on 2013-05-24
As far as I know, Ubuntu 13.04 has Samba 4, while Ubuntu Server should still have Samba 3. The problems could be due to different Samba versions on server and client.

---

### Post by NOTORIOUS VR on 2013-05-29
That would be pretty crazy if they didn't make them compatible (and seemingly unlikely), I wonder if there is some config options that would allow for backwards compatibility?

---

### Post by redmk2 on 2013-05-29
> **NOTORIOUS VR said:**
> That would be pretty crazy if they didn't make them compatible (and seemingly unlikely), I wonder if there is some config options that would allow for backwards compatibility?

Samba4 and Samba3 servers are *both available* with Ubuntu.  The Samba client is compatible with both of them.  The Open Solaris uses  CIFS-Server which is NOT Samba and may not be inter operable without specific configuration.  I believe there is a Samba package still available for Solaris if you need to use that instead of Solaris' CIFS-Server.

---

### Post by NOTORIOUS VR on 2013-05-31
Why would I switch my file server that is working perfectly fine with every other device (phones/tablets, printers, windows, osx, etc) only ubuntu seems to have having this issue.

What I don't understand is, isn't SMB exactly that.. SMB?  Shouldn't they all be compatible?   I mean, it's a standard for a reason, which is exactly why things like my printer, or tablets, media players (Boxee) are able to connect via SMB/Windows Shares just fine.  What I don't understand is why Ubuntu seems to have issues with it.  There must be some conflict or setting.  But maybe this is the wrong forum?  I thought this was a place for support.

---

### Post by redmk2 on 2013-05-31
> **NOTORIOUS VR said:**
> Why would I switch my file server that is working perfectly fine with every other device (phones/tablets, printers, windows, osx, etc) only ubuntu seems to have having this issue.
Who told you to switch to Samba.  Did you miss: [COLOR="#FF0000"]**" may not be inter operable without specific configuration"**[/COLOR]? 
> 

What I don't understand is, isn't SMB exactly that...SMB?  
What, exactly what?  Samba uses multiple protocols.  SMB/CIFS is one.  NetBIOS is another.  NetBIOS over TCP (NBT) is another.  And we haven't even touched upon authentication.  Any of this can be implemented in different ways and still follow the RFC's when there are such things.  In some instances there aren't even RFC's. > 
Shouldn't they all be compatible? 
Not necessarily upon initial installation.   For example the Latest CIFS server created by Apple for OSX is not compatible with Samba by default.  See [**[COLOR="#FF8C00"]here[/COLOR]**]("http://www.zdnet.com/samba-growing-pains-continue-in-os-x-lion-7000001353/")> 

I mean, it's a standard for a reason, which is exactly why things like my printer, or tablets, media players (Boxee) are able to connect via SMB/Windows Shares just fine.  What I don't understand is why Ubuntu seems to have issues with it.  There must be some conflict or setting. 
I think I said that earlier.> 
But maybe this is the wrong forum? 
Possibly.  We don't have all the answers> 
I thought this was a place for support.
Sometimes it's just commiseration here.  ;-)  Nothing official here in the way of support or documentation.

If you want  OpenSolaris support then I would see [**[COLOR="#FF8C00"]OpenIndiana for support[/COLOR]**]("http://wiki.openindiana.org/oi/Using+OpenIndiana+as+a+storage+server") or (gasp!) [Oracle]("http://docs.oracle.com/cd/E19082-01/820-2429/").

---

