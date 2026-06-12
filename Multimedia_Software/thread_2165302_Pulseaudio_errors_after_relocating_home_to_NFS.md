---
title: "Pulseaudio errors after relocating home to NFS"
date: 2013-08-04
forum: Multimedia Software
---

### Post by HomeOnThePlains on 2013-08-04
I've relocated my home to a diff machine using NFS on my small home network (this issue involves two machines both running UbuntuStudio 12.04 LTS). Everything seems fine except Pulseaudio. I'm getting these errors:

[edit 1] This is the output from the volume control: 

"Connection to PulseAudio failed. Automatic retry in 5s

In this case this is likely because PULSE_SERVER in the Environment/X11 Root Window Properties or default-server in client.conf is misconfigured.
This situation can also arrise [sic] when PulseAudio crased and left stale details in the X11 Root Window.
If this is the case, then PulseAudio shoudl autospawn again, or if this is not configured you should run start-pulseaudio-x11 manually."

When I run "start-pulseaudio-x11" this is the output: [end edit 1]

E: [autospawn] core-util.c: Home directory /home/shawn not ours.
W: [autospawn] lock-autospawn.c: Cannot access autospawn lock.
E: [pulseaudio] main.c: Failed to acquire autospawn lock

I believe it may be related to permissions/users, etc but I'm at a loss. Anyone, pls?

---

### Post by Yellow Pasque on 2013-08-04
```
ls -la /home
```

---

### Post by HomeOnThePlains on 2013-08-04
> **Temüjin said:**
> ```
ls -la /home
```

drwxr-xr-x  8 nobody nogroup   4096 Aug  3 06:53 .
drwxr-xr-x 24 root   root      4096 Aug  1 12:19 ..
drwx------  2 nobody nogroup  16384 Aug  2 16:38 lost+found
drwxr-xr-x  2 nobody nogroup   4096 Aug  3 06:53 Movies
drwxr-xr-x  2 nobody nogroup 626688 Aug  3 11:22 Music
drwxr-xr-x 11 nobody nogroup  16384 Aug  3 11:26 Music2
drwxr-xr-x 44 nobody nogroup   4096 Aug  3 12:12 pedro
drwxr-xr-x 58 nobody nogroup   4096 Aug  4 17:53 shawn

---

### Post by Yellow Pasque on 2013-08-04
```
    drwxr-xr-x 58 nobody nogroup 4096 Aug 4 17:53 shawn 
```
^You probably need to fix that..
Normally, the following command would do it, but I'm not familiar with NFS permissions.
```
chown -R shawn:shawn /home/shawn
```

---

### Post by HomeOnThePlains on 2013-08-04
That happens automatically with NFS. On the server I'm the owner:group but on the client mounts NFS changes them to nobody:nogroup. That's why it seems to be a permissions/users issue for pulse. I tried adding the users pulse and pulse-access users to the nogroup group but that didn't work. 

Everything else seems fine. All applications seem fine. Firefox and Thunderbird run with no issues. Terminal is fine.  I can boot and use Windows 7 and Debian 7 XFCE in VirtualBox from the NFS server just fine (except they both complain about no sound at startup). Thanks for the input though.

---

### Post by steeldriver on 2013-08-04
I think that only happens if you are using the all_squash export option on the server to work around inconsistent uids / gids between the client and server, doesn't it? If you have control of both systems, then you can change your uids / gids either on either the client or server so that they are the same, and then set the export to no_all_squash (actually that's the default, I think - so no need to set it explicitly, just remove the all_squash otion)

From **man exports**:
```

       all_squash
              Map  all  uids  and  gids to the anonymous user. Useful for NFS-
              exported public FTP directories, news  spool  directories,  etc.
              The  opposite option is no_all_squash, which is the default set&#8208;
              ting.

```

---

### Post by HomeOnThePlains on 2013-08-04
> **steeldriver said:**
> I think that only happens if you are using the all_squash export option on the server to work around inconsistent uids / gids between the client and server, doesn't it? If you have control of both systems, then you can change your uids / gids either on either the client or server so that they are the same, and then set the export to no_all_squash (actually that's the default, I think - so no need to set it explicitly, just remove the all_squash otion)

From **man exports**:
```

       all_squash
              Map  all  uids  and  gids to the anonymous user. Useful for NFS-
              exported public FTP directories, news  spool  directories,  etc.
              The  opposite option is no_all_squash, which is the default set&#8208;
              ting.

```

My only export options are (rw,sync) so therefore I'd be defaulting to no_all_squash, right? I'll try it with the no_all_squash explicitly and see what happens.

Edit: Tried explicit no_all_squash and NFS still changes all exports (on clients) to nobody:nogroup. Thanks for the suggestion though.

Edit2:  I'm leaning more towards users/perms for sure now because I've discovered since my original post that synaptic and gparted will not boot after authentication. I'll keep digging and update if I figure this out.

---

### Post by SeijiSensei on 2013-08-05
Do you have identical user and group IDs in /etc/passwd and /etc/group on both machines?  Remember that usernames like "shawn" are just a convenience.  Permissions depend on the UID and GID values.  If "shawn" has ID 1000 on one machine and 1001 on another, you'll have permission problems.  There are solutions for this like idmapd, but just maintaining identical /etc/passwd and /etc/group files works best on small networks.

---

### Post by HomeOnThePlains on 2013-08-07
> **SeijiSensei said:**
> Do you have identical user and group IDs in /etc/passwd and /etc/group on both machines?  Remember that usernames like "shawn" are just a convenience.  Permissions depend on the UID and GID values.  If "shawn" has ID 1000 on one machine and 1001 on another, you'll have permission problems.  There are solutions for this like idmapd, but just maintaining identical /etc/passwd and /etc/group files works best on small networks.

Thnx for the response. The personal U and GIDs matched, yes, and most other users as well (including pulse). Because I don't have the time to fart around too much with this, rather than share my personal user homes I'm going to make homes for the Movies and Music dirs and share them. This *should* be simpler and will satisfy my needs for now. I appreciate the responses.

---

