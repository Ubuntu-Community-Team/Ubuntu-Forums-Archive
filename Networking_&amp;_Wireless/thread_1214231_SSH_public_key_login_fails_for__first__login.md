---
title: "SSH public key login fails for _first_ login"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by VaqTim on 2009-07-15
Hello all !
 
I'm trying to set up an Ubuntu (Jaunty) system as a low-power remote system - meaning that I want to turn it on and off over LAN. Automatically, from my Windows system. The WOL I've got working. I have a problem shutting down.
 
I'm using PuTTY, and want to use Plink with an unsigned private key (this is my LAN at home, okay ?). I've set everything up, using PuttyGen SSH-RSA 2 keys, and it all works fine. Public keys are in /.ssh/authorized_keys with chmod 600, sshd_config uses PubkeyAuthentication, and the AuthorizedKeysFile points to %h/.ssh/authorized_keys. Putty/plink is set up to access the private key file directly.
 
So, yes, it all works nicely and I can log in to my account without password verification quite nicely.
 
UNLESS that is, I am not logged in already (either remotely or in a GNOME session - the server is not remote yet !). I this case, I get the dreaded "Server refused our key" message.
 
Here's a bit of auth.log for a succesful login
```
 
Jul 15 20:42:39 BackUpper sshd[12178]: debug1: Client protocol version 2.0; client software version PuTTY_Release_0.60
Jul 15 20:42:39 BackUpper sshd[12178]: debug1: no match: PuTTY_Release_0.60
Jul 15 20:42:39 BackUpper sshd[12178]: debug1: Enabling compatibility mode for protocol 2.0
Jul 15 20:42:39 BackUpper sshd[12178]: debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
Jul 15 20:42:45 BackUpper sshd[12178]: debug1: PAM: initializing for "tim"
Jul 15 20:42:45 BackUpper sshd[12178]: debug1: PAM: setting PAM_RHOST to "192.168.0.12"
Jul 15 20:42:45 BackUpper sshd[12178]: debug1: PAM: setting PAM_TTY to "ssh"
Jul 15 20:42:45 BackUpper sshd[12178]: Failed none for tim from 192.168.0.12 port 3564 ssh2
Jul 15 20:42:45 BackUpper sshd[12178]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-1024
Jul 15 20:42:45 BackUpper sshd[12178]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-1024
Jul 15 20:42:45 BackUpper sshd[12178]: debug1: temporarily_use_uid: 1000/1000 (e=0/0)
Jul 15 20:42:45 BackUpper sshd[12178]: debug1: trying public key file /home/tim/.ssh/authorized_keys
Jul 15 20:42:45 BackUpper sshd[12178]: debug1: fd 4 clearing O_NONBLOCK
Jul 15 20:42:45 BackUpper sshd[12178]: debug1: matching key found: file /home/tim/.ssh/authorized_keys, line 1
Jul 15 20:42:45 BackUpper sshd[12178]: Found matching RSA key: XXXX
Jul 15 20:42:45 BackUpper sshd[12178]: debug1: restore_uid: 0/0
Jul 15 20:42:51 BackUpper sshd[12178]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-1024
Jul 15 20:42:51 BackUpper sshd[12178]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-1024

```
 
and here's a bit of the failed login :-
 
```
Jul 15 20:37:57 BackUpper sshd[11641]: debug1: Client protocol version 2.0; client software version PuTTY_Release_0.60
Jul 15 20:37:57 BackUpper sshd[11641]: debug1: no match: PuTTY_Release_0.60
Jul 15 20:37:57 BackUpper sshd[11641]: debug1: Enabling compatibility mode for protocol 2.0
Jul 15 20:37:57 BackUpper sshd[11641]: debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
Jul 15 20:38:02 BackUpper sshd[11641]: debug1: PAM: initializing for "tim"
Jul 15 20:38:02 BackUpper sshd[11641]: debug1: PAM: setting PAM_RHOST to "192.168.0.12"
Jul 15 20:38:02 BackUpper sshd[11641]: debug1: PAM: setting PAM_TTY to "ssh"
Jul 15 20:38:02 BackUpper sshd[11641]: Failed none for tim from 192.168.0.12 port 3559 ssh2
Jul 15 20:38:02 BackUpper sshd[11641]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-1024
Jul 15 20:38:02 BackUpper sshd[11641]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-1024
Jul 15 20:38:02 BackUpper sshd[11641]: debug1: temporarily_use_uid: 1000/1000 (e=0/0)
Jul 15 20:38:02 BackUpper sshd[11641]: debug1: trying public key file /home/tim/.ssh/authorized_keys
Jul 15 20:38:02 BackUpper sshd[11641]: debug1: restore_uid: 0/0
Jul 15 20:38:02 BackUpper sshd[11641]: debug1: temporarily_use_uid: 1000/1000 (e=0/0)
Jul 15 20:38:02 BackUpper sshd[11641]: debug1: trying public key file /home/tim/.ssh/authorized_keys
Jul 15 20:38:02 BackUpper sshd[11641]: debug1: restore_uid: 0/0
Jul 15 20:38:02 BackUpper sshd[11641]: Failed publickey for tim from 192.168.0.12 port 3559 ssh2

```
 
I can see that the failed lookup has no "fd 4 clearing O_NONBLOCK" entry - though I have no idea what this could mean.
 
Does that give anyone any clues ?
 
I want to have totally automated accessed to the system (primarily to do backups) so I don't want to have to remember to log in manually all the time.
 
Can anyone think of any workarounds ? 
 
Maybe there's a plink equivalent that will let you put your password on the command line ! At least it would get things working for me !
 
Tim

---

### Post by Wibb-untu on 2009-08-08
I have been struggling for a while trying to work out why this happens. So I've registered especially to help anyone with the same problem.

I found the solution/workaround here:
[http://www.mail-archive.com/ecryptfs@lists.launchpad.net/msg00923.html](http://www.mail-archive.com/ecryptfs@lists.launchpad.net/msg00923.html)

In short: 
As I understand things, you probably have encrypted home directories.
This means public keys in the .ssh folder are encrypted and sshd can't read them.

Once you log in, the home directory is unencrypted and the public keys are readable - hence, if you make a new session and log in again, the public key will be recognised.

Workaround: 
make a new .ssh public keys folder outside of your home directory with your username, like
/etc/.ssh/<username>/authorized_keys and stick your public key in there. Don't forget to chown the user folder there with only user permissions, same for the authorized_keys file.

in your sshd_config file, change your AuthorizedKeysFile line to read something like
AuthorizedKeysFile      /etc/.ssh/%u/authorized_keys

So now sshd will be reading an authorized_keys file which is not encrypted. Problem solved - hopefully! :P

---

