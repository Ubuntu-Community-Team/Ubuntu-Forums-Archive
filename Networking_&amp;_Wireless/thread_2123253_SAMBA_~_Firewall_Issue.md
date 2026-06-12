---
title: "SAMBA ~ Firewall Issue"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by mike acker on 2013-03-07
after cussing at SAMBA for MONTHS I discovered it is the default firewall that is stopping Windows Computers from accessing even the most basic share.

In the BASIC Ubuntu/Samba document [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)

there should be a leading paragraph regaarding FIREWALLs

note: I'm using the basic firewall UFW from the U/Software Centre

~~~

Now then: the Important Question : how do I correct that UFW configuration so that Samba is allowed on the local / internal Wi-Fi net ONLY ?

i have the UFW Firewall set to OFF now -- and the system still passes Steve Gibson's port probe,...  do I really need the firewall ?

---

### Post by Morbius1 on 2013-03-07
>  i have the UFW Firewall set to OFF now -- and the system still passes  Steve Gibson's port probe,...  do I really need the firewall ?                 
If you are using Samba you have a local network. If you have a local network you are behind a router. If you have a router Gibson's port probe is probing the router not the machines behind the router. There's no way to probe the ports on an ip address behind the router since they aren't public ip addresses - nobody knows you exist. Do you need a firewall? Not as long as you are behind your router. So it comes down to what kind of machine you are using. If it's a desktop and you are always behind the router I would argue you don't deed one. If it's a laptop that could end up anywhere then you do - or you can enable it when you are out and about and disable it when you are home.
>  Now then: the Important Question : how do I correct that UFW  configuration so that Samba is allowed on the local / internal Wi-Fi net  ONLY ?
You could allow Samba for everyone and use Samba to determine who can access it. You can do that by adding a line to your /etc/samba/smb.conf file in the [global] section:
```
hosts allow = something
```
"something" can be specific ip addresses, a range of ip addresses, all of the ip addresses on your local lan, specific host names, etc ... See man smb.conf
>  In the BASIC Ubuntu/Samba document [https://help.ubuntu.com/12.04/server...ileserver.html]("https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html")
That HowTo either needs to be taken down or submitted for peer review. It's factually incorrect ( "security = user" does not need to be un-commented ) and it produces a guest share that will break the instant the user creates a private share requiring authentication. All it needs is one line added to fix.

---

### Post by mike acker on 2013-03-07
~ thank you for a very thoughtful and helpful reply . i will take each point under consideration,--

i did in fact re-comment the security = user line in my desperate attempt to get Samba working . i'm working on a huge photo project and i have to scan on my old Windows machine because my Epson V500 is not supported on Linux ( ex 3d party package which i hesitate to install ) .  

anyway i got to the point where taking 4 hours of bad medicine with Samba was better than using a USB flash drive sneakers net

i'm using an E900  CICSO LINKSYS wireless router w/ WPA2

---

### Post by Morbius1 on 2013-03-07
> **mike acker said:**
> i did in fact re-comment the security = user line 
It actually makes no difference if you comment it out or not. smb.conf even tells you that:
> # Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
[COLOR=#0000cd][B]#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here[/B][/COLOR]

"secrity = user" is preceded by a '#' sign indicating that it is already the default setting. Smb.conf is not the samba config file. It's a set of additions and overrides to the default settings of samba. The HowTo author's insistence that it be uncommented is not factually correct.

Things like that bug me, sorry.

---

### Post by pdc on 2013-03-07
Hi Mike; I am always keen to follow threads on such things as Samba;

as an aside, I noted you said "[COLOR="#EE82EE"]my Epson V500 is not supported on Linux[/COLOR]"

If I go to the Epson site, [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and enter V500 it takes me to

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21580&DSCCHK=ea245da3525f56d8ca2ab9408ed2d6d8b481d435](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21580&DSCCHK=ea245da3525f56d8ca2ab9408ed2d6d8b481d435) 

where Epson supply 3 things for your V500

1) a data package [COLOR="#008000"]iscan-data_1.22.0-1_all.deb[/COLOR] (INSTALL FIRST)
2) deb packages for ubuntu, in 32bit or 64bit flavours;  it is [COLOR="#008000"]iscan_2.29.1-5~usb0.1.ltdl7_i386.deb[/COLOR] for 32bit ........or [COLOR="#008000"]iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb[/COLOR]
3) plug-in package [COLOR="#008000"]iscan-plugin-gt-x770_2.1.2-1_i386.deb[/COLOR] or [COLOR="#008000"]iscan-plugin-gt-x770_2.1.2-1_amd64.deb[/COLOR]

I include a thumbnail of the download window

---

### Post by mike acker on 2013-03-09
> **pdc said:**
> Hi Mike; I am always keen to follow threads on such things as Samba;

as an aside, I noted you said "[COLOR=#EE82EE]my Epson V500 is not supported on Linux[/COLOR]"

If I go to the Epson site, [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and enter V500 it takes me to

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21580&DSCCHK=ea245da3525f56d8ca2ab9408ed2d6d8b481d435](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21580&DSCCHK=ea245da3525f56d8ca2ab9408ed2d6d8b481d435) 

where Epson supply 3 things for your V500

1) a data package [COLOR=#008000]iscan-data_1.22.0-1_all.deb[/COLOR] (INSTALL FIRST)
2) deb packages for ubuntu, in 32bit or 64bit flavours;  it is [COLOR=#008000]iscan_2.29.1-5~usb0.1.ltdl7_i386.deb[/COLOR] for 32bit ........or [COLOR=#008000]iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb[/COLOR]
3) plug-in package [COLOR=#008000]iscan-plugin-gt-x770_2.1.2-1_i386.deb[/COLOR] or [COLOR=#008000]iscan-plugin-gt-x770_2.1.2-1_amd64.deb[/COLOR]

I include a thumbnail of the download window

thanks!!  I'll have to check this out!!

---

### Post by mike acker on 2013-03-09
as far as I'm concerned: "samba" needs to go into the garbage. we need to start over and create a package that is
[LIST]
[*]easy to configure 
[*]reliable 
[/LIST]

my daughter is here for help with er homework and guess what: Samba has a flat tire again: no communications from her windows machine -- although I had it working OK earlier today.   all she did was sign on with her own user ID on the windows box .

---

### Post by Morbius1 on 2013-03-09
> all she did was sign on with her own user ID on the windows box
Did you ever create a user on the Ubuntu server for her and then add her to the samba password database? If you did the share you created will not allow write access.

That HowTo has you:

** Create a directory at /srv/samba/share
** Change ownership to nobody:nogroup
** What's not stated explicitly is the permissions are automatically set to 755.
** Then he has you create the share:
> 
[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755
If you ever create a share that requires credentials or in the case of a Windows client ever create a Linux user for that Windows user and give her a samba password then they are no longer "nobody". They are somebody and they will no longer have write access.

It's a bad HowTo which is why I stated earlier that they either need to take it down or open it up to peer review so that it can be fixed. There are a hundred ways to fix it but one of the easiest ways is to add one line to the share definition:
> 
[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
[COLOR=#0000cd]**    force user = nobody**[/COLOR]
    create mask = 0755
Then restart samba:
```
sudo service smbd restart
```

---

### Post by mike acker on 2013-03-10
> **Morbius1 said:**
> Did you ever create a user on the Ubuntu server for her and then add her to the samba password database? If you did the share you created will not allow write access.

That HowTo has you:

** Create a directory at /srv/samba/share
** Change ownership to nobody:nogroup
** What's not stated explicitly is the permissions are automatically set to 755.
** Then he has you create the share:

If you ever create a share that requires credentials or in the case of a Windows client ever create a Linux user for that Windows user and give her a samba password then they are no longer "nobody". They are somebody and they will no longer have write access.

It's a bad HowTo which is why I stated earlier that they either need to take it down or open it up to peer review so that it can be fixed. There are a hundred ways to fix it but one of the easiest ways is to add one line to the share definition:

Then restart samba:
```
sudo service smbd restart
```

thanks for being patient with me!!
yes: she does have a log-on for the Ubuntu computer -- and for Windows
```

# (smbusers)
# ubuntuuserid = "WindowsUserID"
jennifer = "Jennifer"

```

i think i added her with smbpassword -- how do i check that ? pdbedit shows she does have a user id
when she logs onto Windows -- she does not see the *nix box under networks

i just re-checked this this morning: although my windows logon finds the *nix box -- hers does not
~~~

I agree with you on the how-to for Samba. one of the thngs i've noticed about Ubuntu/Linux is it's importatn to have documentation for the exact version that is being used.

~~~
my original thinking on Samba was that I would (1) create a Ubuntu User ID for her and then allow her to connect to that from her Windows machine. access should then be the same as if she logged onto the Ubuntu machine directly .

Amendment:

I think I found the problem : in the Windows computer I turned "Network Discovery" on in the Control Panel in the Home Networks section ***using her logon***.  Now she has access.

This is the reason why that Howto document needs to be peer reviewed: information is missing/inaccurate. at this point it appears the problem is the how-to document rather than the software.

---

