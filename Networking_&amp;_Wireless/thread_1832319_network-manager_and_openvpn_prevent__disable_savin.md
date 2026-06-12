---
title: "network-manager and openvpn: prevent / disable saving the private key password"
date: 2011-08-24
forum: Networking &amp; Wireless
---

### Post by derekshaw on 2011-08-24
OK -- this is a pretty simple statement of the problem, with an incomplete solution.
[http://ubuntuforums.org/showthread.php?p=11183389](http://ubuntuforums.org/showthread.php?p=11183389)

I work with ordinary users who look for shortcuts.  If they can save entering a password by storing it, they will.  Just to be clear about the thinking behind this: the keyring provides no protection -- the users have already written down the password to log on to the laptop somewhere, or they changed their password and then had to googled how fix it, leaving the keyring unprotected(1).  With the private key no longer private, a lost or stolen laptop, or one played with by the kids at home, becomes a potentially-fatal hole into the LAN it is connecting to, for as long as we don't know that the laptop is lost, stolen, or being used by the kids (sure, that's covered in the AUP, but it's still a hole).

So let's not create booby-traps for them to fall into.  Let's help keep them on the "straight and narrow".

I need a way to actually prevent my users from saving the decryption password for the openVPN private key certificate (called the "private key password" in the configure dialogue for openVPN connections).

I don't want to prejudice any workable solutions, but the way I see it is that there are two ways for users to save the private key password (I am sure there are others).  Blocking these two would be a critical first step.

The first one is to prevent the password being saved when the user authenticates the VPN connection (this is the problem with the solution to the thread created earlier and marked solved).  To describe this another way -- if you have followed the solution in the quoted thread, the next time you choose the VPN connection, it will ask for the password, AND OFFER TO SAVE IT IN THE KEYRING.  This dialogue box is called "Authenticate VPN".  A half-way acceptible kludge would be if gconf-editor made it possible to hide the checkbox labelled "Save password in keyring".

The other place to block the saving of the password is in the creation of the VPN connection (Edit Connections --> VPN --> Add).  The field labelled "Private Key Password" needs to be hidden.

Another possibility is to remove the saved password from the keyring at the time of logout (there is a place to run commands like this).  I tried removing the keyrings this way, but that generates more problems than it solves.

I am reluctant to start using the command-line method for users to establish the vpn, because eventually some bright spark will figure out how to do it with network-manager, and tell everyone else.

Anybody got any ideas?

Thanks in advance!
d.

(1) like he says in this link, it's stupid easy, and impossible to prevent.
[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

---

