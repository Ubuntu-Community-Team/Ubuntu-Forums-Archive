---
title: "Can a windows client connect to a vino server?"
date: 2012-07-31
forum: Networking &amp; Wireless
---

### Post by MakOwner on 2012-07-31
Is it possible for vino, or any other VNC variant provide a remote desktop capability from a gnome desktop to a windows client?

If I set up and enable vino, can I use a Windows VNC client to access the shared desktop?

Hopefully there is a VNC server that will allow a windows RDP client to connect, but if not I need an installable windows client - but not the whole Cygwin thing.  Way too complicated setup for the target audience.

---

### Post by joco1500 on 2012-07-31
I do believe so

---

### Post by steeldriver on 2012-07-31
If you really want to connect from the native Windows 'Remote Desktop Connection' then you can give xrdp a try

Otherwise I've had good luck with both TightVNC and UltraVNC Windows clients

---

### Post by MakOwner on 2012-07-31
Thanks for the tips - this will help, thanks!

---

### Post by wildmanne39 on 2012-08-01
*Thread moved to **Networking & Wireless**.*

---

### Post by MakOwner on 2012-08-01
> **wildmanne39 said:**
> *Thread moved to **Networking & Wireless**.*

Thank you for moving this to the appropriate forum.

---

### Post by MakOwner on 2012-08-01
> **steeldriver said:**
> If you really want to connect from the native Windows 'Remote Desktop Connection' then you can give xrdp a try

Otherwise I've had good luck with both TightVNC and UltraVNC Windows clients

I have loaded TightVNC client on windows, and I can connect to the Linux box after I have manually started the vino server after logging in.

Is there anyway to set the vino server up as a service so that multiple clients can connecot simultaneously, ala Windows Terminal Services?

---

### Post by MakOwner on 2012-08-01
> **MakOwner said:**
> I have loaded TightVNC client on windows, and I can connect to the Linux box after I have manually started the vino server after logging in.

Is there anyway to set the vino server up as a service so that multiple clients can connecot simultaneously, ala Windows Terminal Services?

EDIT:
I think what I'm looking for is a remote gdm login, but the clients have to be windows.  bleh.  Adding a monolithic install package like tightvnc is acceptable for the target audience.  Will tight/real/whatever vnc viewer clients operate like that from Windows?

---

### Post by MakOwner on 2012-08-01
Found this set of instructions on making VNC work with GDM.
(I'm using Mint Mate 13 on this desktop that will be used as a "jump host" into a protected network).

This is pretty generic.  Hopefully someone around here has done this before and can tell me if this worked for them?

Edit: Link to original: [http://commons.oreilly.com/wiki/index.php/Linux_in_a_Windows_World/Remote_Login_Tools/Running_GUI_Programs_Remotely](http://commons.oreilly.com/wiki/index.php/Linux_in_a_Windows_World/Remote_Login_Tools/Running_GUI_Programs_Remotely)


 Linking VNC to an XDMCP server

The usual mode of VNC's operation is peculiar by Linux server standards. Instead of connecting to the server using a fixed port and entering a username and password to gain entry, you must log in using a text-mode tool or run the server while you're at the console, then connect using a port number that you must remember and enter a password (but no username). This approach certainly works, but it can be a bit awkward if arbitrary users should have access to the VNC server. To work around this problem and create a more typical Linux-style login experience, you can tie VNC to an XDMCP server. The result is that, when users connect to the VNC server, they'll be greeted by a GUI login screen that's similar to the one they see when logging in at the console or via an XDMCP-enabled remote X server.

Before proceeding, check the earlier Section 11.2.5. You should configure your XDMCP server to accept remote connections, with one possible exception: you can use Xaccess rules or firewall rules to restrict XDMCP access to the local computer itself. Both the XDMCP server and the VNC server will be running on the same computer, and the XDMCP server only needs to accept connections from the VNC server. You can configure the XDMCP server to be more promiscuous in the connections it accepts, but if this isn't necessary, it can be a bit of a security risk, particularly if the computer is accessible to the world at large, and you use firewall rules or super server security settings to restrict access to the VNC server.

Once you've configured the XDMCP server, you should edit your /etc/services file. This file gives names to various TCP and UDP ports. You should add entries for any ports you want to assign to VNC. The names you use are arbitrary, but vnc or something related to it is a logical choice. Note that you can use just one port or many ports. Using many ports lets you run multiple VNC servers with different options&#8212;for instance, to run servers with different virtual screen resolutions for the benefit of clients with different screen resolutions. For example, suppose you intend to run VNC with 760 530 and 950 700 resolutions. First, create two entries in /etc/services:

vnc-760x530   5900/tcp
vnc-950x700   5901/tcp

This configuration assigns TCP ports 5900 and 5901 to VNC, using names that describe the intended uses for these ports as supporting different resolutions.

Once this is done, edit your super server configuration to call the Xvnc server. This call must include several parameters that are normally handled by the vncserver script, such as -geometry, -depth, and -fp. Other options that may be necessary include:

    session-num 

    This option specifies the X session number; each unique X session needs its own session number. Note that this is an X session number, not a VNC session number. If your system normally runs a local X server, begin with :1. You can also begin with :0 if no conventional local X server ever runs on the system. Some systems work best if you omit the X session number, enabling VNC to pick one dynamically. 
-ac
    This option disables access controls in TightVNC&#8212;that is, the initial password request. Because XDMCP handles this task, disabling the initial VNC password request is desirable. Some VNC versions don't need or support this option, though; they use the -SecurityTypes option instead or disable access controls as a side effect of other settings necessary for this configuration. 
-SecurityTypes=none
    This option is RealVNC's equivalent of TightVNC's -ac option. 
-once
    Ordinarily, a VNC server runs until killed; even if you disconnect from the server, it continues to run. This option causes the server to terminate after a connection is lost. Its behavior is desirable when VNC is used with XDMCP because it better implements the traditional Linux login/logoff procedures. 
-inetd
    This option tells Xvnc that it's running from a super server. 
-query localhost
    This option speaks to the VNC server's X server side; it tells the server to contact a specific computer for an XDMCP login. In this case, the server contacted is localhost, which should work well. You can use 127.0.0.1 or your computer's external IP address or hostname if you prefer. (Using localhost or 127.0.0.1 may result in slightly better performance, though.) 

To produce a xinetd configuration incorporating these elements, create the file /etc/xinetd.d/vnc. This file should have one or more entries like this:

service vnc-760x530
{
   disable      = no
   socket_type  = stream
   protocol     = tcp
   wait         = no
   user         = nobody
   server       = /usr/bin/Xvnc
   server_args  = :1 -inetd -query localhost -geometry 760x530 \
                  -depth 24 -ac -once \
                  -fp /usr/share/fonts/misc/,/usr/share/fonts/100dpi/
}

Tip

The large number of arguments passed to Xvnc dictates splitting them across three lines in this book; however, they should all be entered on a single line in reality. Backslash characters (\) denote continued lines here but should not be entered in your real configuration files.

You may need to experiment with the -ac and -SecurityType parameters to get this to work. Your font path is also likely to be longer than the one shown here. Some distributions, such as Fedora, provide a font server for local use, which can greatly shorten the font path entry, but the entry is likely to read unix/:7100.

After restarting your super server, the VNC server should become available to VNC clients, as described in Section 11.4.4. You'll notice several differences in how VNC behaves, though:

    Multiple users can log into a single VNC port.
    Users don't need to explicitly configure their VNC sessions.
    Users' VNC logins produce their standard desktop environments, as set by X system defaults and users' own options.
    Sessions are destroyed when users log out; they must save open files or their unsaved work will be lost.
    Users don't enter VNC passwords, but they have to enter a password at the XDMCP login prompt.
    If you set up multiple VNC ports to accept logins with different parameters, the VNC session number controls access to the options you set. For instance, connecting to pluto:0 could yield a 760 530 display, whereas connecting to pluto:1 can produce a 950 700 display. 

Overall, linking VNC to an XDMCP server can be an excellent way to provide remote GUI logins to a Linux system. This approach follows typical expectations for GUI logins and works much like accessing Linux via a rooted X server using XDMCP. VNC client software is inexpensive and easier to configure than X servers, though, which can simplify your overall configuration and education efforts, even if linking VNC with XDMCP is a bit more work.

Warning

One downside to this approach is that usernames and passwords sent to the XDMCP server are unencrypted. (Ordinary VNC passwords are encrypted, although the rest of the session data is not.) Given that most VNC data isn't encrypted, this isn't a huge difference, but it is worth noting and may make a difference in your plans, particularly if you want to use VNC across the Internet.

---

### Post by MakOwner on 2012-08-01
I'm talking to myslef here a lot lately ...

I have vino working and can get to a remote desktop session after I have logged in and started the vino server.
I found these instructions on how to get the session working from the mdm login prompt:
```

First of all, you must configure your vino server by running vino-preferences as root.
Then, append the line
/usr/lib/vino/vino-server --sm-disable &
in file /etc/gdm3/Init/Default
before the line 'exit 0'
And finally, you must prevent vino from being run second time after logging in by disabling it's autorun in Menu -> Preferences->Startup Applicationsd

```

And it worked! - sort of...
I reboot the workstation and I can use tightvnc viewer to connect to the box (that's good!) and I can enter a user id and password, but after pressing enter, the connection is terminate and vino is no longer running, and I can't connect again until I reboot. (that's bad!)

I'm almost there! Can anyone help over the last little bit?

---

