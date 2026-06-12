---
title: "ftp authentication error"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by snipe34 on 2011-06-13
Hi,

I'm troubleshooting a windows problem and I noticed this is the auth.log on my server (Ubuntu 10.04).  It has nothing to do with the windows problem and it doesn't bother the ftp connection between the windows box and the server.  


Jun 13 14:51:52 ubuntu-server vsftpd: pam_unix(vsftpd:auth): authentication failure; logname= uid=0 euid=0 tty=ftp ruser=ftp rhost=192.168.0.100  user=ftp
Jun 13 14:51:52 ubuntu-server vsftpd: pam_winbind(vsftpd:auth): getting password (0x00000388)
Jun 13 14:51:52 ubuntu-server vsftpd: pam_winbind(vsftpd:auth): pam_get_item returned a password
Jun 13 14:51:52 ubuntu-server vsftpd: pam_winbind(vsftpd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user


It seems to happen every time I connect to the server from the windows box.  It seems like something is only partially  configured, but what??  I only use the ftp as part of my backup, so I could change it over to samba and be done with it.

Any ideas?

Thanks,
Tim

---

### Post by luvshines on 2011-06-14
Looks like winbind appears in your pam files.
You may grep for pam_winbind.so in /etc/pam.d directory.

If you are not using it, you may purge it and it should be gone

---

### Post by snipe34 on 2011-06-14
Hi,

I'm using winbind.  

Looking around I found a typo in /etc/nsswitch.conf  -  was windbind instead of winbind.  Doesn't seem to be making any difference with the ftp authentication error.

---

### Post by luvshines on 2011-06-15
> **snipe34 said:**
> Hi,

I'm using winbind.  

Looking around I found a typo in /etc/nsswitch.conf  -  was windbind instead of winbind.  Doesn't seem to be making any difference with the ftp authentication error.

You are using winbind for CIFS acess with AD users ??

If you try to access samba shares with same user, do you see similar errors ?

---

### Post by snipe34 on 2011-06-15
That may be what's generating the error.  If I recall winbind was installed when I was getting samba to work with my one Windows 7 machine, I know I didn't do anything with Active Directory.  So I guess winbind is running without a proper configuration.  So I guess I will need to set samba up as a domain controller.  It's sort of half configured that way anyway.  Do I really need to, I don't have a Windows AD domain?  Or should I try backing up the configuration files and purging winbind?

I tried stopping winbind, but that just generated different errors using ftp access having to do with winbind not running  But it didn't stop the ftp access.

The user for ftp access is not part of the group of samba users.

I did notice these errors in syslog.  They repeat 3 or 4 times (or more) and then go quiet for hours.  This seems to be related to samba not ftp.

winbindd[26918]: [2011/06/15 22:40:46,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
winbindd[26918]:   idmap_alloc module tdb already registered!
winbindd[26918]: [2011/06/15 22:40:46,  0] winbindd/idmap.c:149(smb_register_idmap)
winbindd[26918]:   Idmap module passdb already registered!
winbindd[26918]: [2011/06/15 22:40:46,  0] winbindd/idmap.c:149(smb_register_idmap)
winbindd[26918]:   Idmap module nss already registered!

---

### Post by luvshines on 2011-06-17
I think since you have mentioned winbind in nsswitch.conf, it's going for pam_winbind
Try this, if you are not using winbind, just remove winbind from nsswitch, don't touch the pam files and check if it breaks anything.
If all works fine, then let it be that way and reconfigure the system to not start winbind on any run level.
If some protocol access stops working, then put back winbind in nsswitch and post the error message here.

---

### Post by snipe34 on 2011-06-17
I removed winbind from the nsswitch.conf and it did seem to bother anything.  So I stopped winbind and tried to connect from the windows box via ftp.  It still connects but now a different error shows up:

vsftpd: pam_winbind(vsftpd:auth): internal module error (retval = PAM_AUTHINFO_UNAVAIL(9), user = 'ftp')

instead of the previous: 

vsftpd: pam_winbind(vsftpd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user

This seems to indicate to me that winbind is needed.  I turned winbind back on and added it back into the /etc/nsswitch.conf.

I looked at vsftpd.conf, but other than pointing at a non-existent RSA certificate there isn't a lot going on there.

If I ftp in from a terminal on the server there is no log activity and it logs in with no problems. Sorry it's the same log activity as the laptop below.

I tried connecting from a laptop with Ubuntu 11.04 both terminal and nautilus and it connects fine, with no log activity other than 
vsftpd: pam_sm_authenticate: Called
vsftpd: pam_sm_authenticate: username = [xxx]

Seems like it might be an issue with how windows is connecting.

---

### Post by luvshines on 2011-06-19
After you removed winbind from nsswitch.conf, did you restart ftp service ?

---

### Post by snipe34 on 2011-06-19
I was pretty sure I restarted the ftp service, but I just double checked again.  Removing winbind and restarting vsftpd doesn't make any difference with the error.

I added the ssl entries and fixed the certificate entry in vsftpd last night and installed a secure ftp client on the windows box.  That works fine, of course, it doesn't use the vsftpd log in. It uses pam:unix(sshd:session).

I checked the windows box ftp log in from a command prompt/terminal and that works with no errors.

I only use the ftp connection as part of a backup set on the windows box that runs 2x a month.  So the error could have been there all along.  I checked the old logs and its there occasionally, but not when the backup should have been running.  

I thought I was having a problem with the backup software, but it turned out to be a problem with how windows was authenticating with my NAS adapter.  All of the sudden I couldn't read or write to the folders on the attached drive.  I could see the folders, but the connection kept resetting.  All of my Ubuntu machines connected to the NAS adapter and could r/w just fine.  That's why I noticed the error in the logs, I was looking to see if anything was going on with the server when I connected to the NAS.

I never figured out what was going on with windows, I just pulled the NAS adapted and plugged the drive directly into the server.  Saved the current backup sets, reformat the drive to a saner file system and redirect all the backup jobs.  I just triggered a manual run of the ftp backup job from the windows box and it's running without the error. 

I'm thinking the error has something to do with how windows explorer communicates/autheniticates.

Sorry for the long winded response.

---

### Post by snipe34 on 2011-06-29
I'm going to go ahead and mark this as solved.  

I did a clean install of 11.04 and, after getting everything reconfigured, I can no longer generate the error.

Thanks for the help.

---

