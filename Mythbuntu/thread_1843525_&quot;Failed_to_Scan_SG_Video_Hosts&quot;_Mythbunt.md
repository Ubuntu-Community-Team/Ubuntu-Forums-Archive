---
title: "&quot;Failed to Scan SG Video Hosts&quot; Mythbuntu 11.04"
date: 2011-09-13
forum: Mythbuntu
---

### Post by drifting on 2011-09-13
"Failed to Scan SG Video Hosts. <Master Backend Server Name> If they no longer exist please remove them"

Very confused about this, as there are a number of videos that appear in the list, it is just that I cannot add anymore. I have no idea when this problem started, so could have been anytime since my forced upgrade from 10.4 all due to Sat Cards :-)

Did a google and found a couple of comments, but one thing I am sure of, that I will never edit MQSQL directly unless told how!

Any help appreciated

Regards Paul

---

### Post by nickrout on 2011-09-13
Check that your storage groups still exist, are mounted, and have correct permissions.

---

### Post by drifting on 2011-09-13
Well there ends a tale. My music and pictures are fine as they are shared via SMB and fstab mapping on frontends. 
However the videos were working via the new sg system implemented, I seem to recall that you can still do it that way, but seem to remember some caveats.
The drive with the videos is fine, I can even play back existing videos from the drive. So this seems a myth issue on the sg group sharing?

Regards Paul

---

### Post by nickrout on 2011-09-13
Where is the error message coming from?

When does it occur?

What are your videos storage groups set to in the backend setup?

Check that those direcotires are (a) available to the system; and (b) have no permissions problems.

Precise questions, please provide precise answers.

---

### Post by drifting on 2011-09-13
Hi Nick

The drive is there, I can access existing videos from the combined back and frontend. 
The SG for videos is correct and available. The error message is from all the frontends when trying to rescan the video store. This drive and the specific directory is not run via a share, but rather using the new myth sharing.
I might just go back to the old way of accessing the video files via an SMB share.

Regards Paul

---

### Post by nickrout on 2011-09-14
> **drifting said:**
> Hi Nick

The drive is there, I can access existing videos from the combined back and frontend. 
The SG for videos is correct and available. The error message is from all the frontends when trying to rescan the video store. This drive and the specific directory is not run via a share, but rather using the new myth sharing.
I might just go back to the old way of accessing the video files via an SMB share.

Regards Paul

SGs are hardly new :)

I asked about permissions, you haven't answered.

I am unsure which user needs access to the SG directory, mythtv (which runs the backend) or the user that runs the frontend (typically the user that you set up on install). It MAY be that your old videos were created with the correct ownership/permissions, but you have created the new ones with the wrong ownership/permissions.

I would look at the output of ```
ls -l /path/to/sg/filethatcanbeseen.avi
ls -l /path/to/sg/filethatcannotbeseen.avi
```

See if there is a difference.

---

### Post by drifting on 2011-09-14
> **nickrout said:**
> SGs are hardly new :)

I asked about permissions, you haven't answered.



Hi Nick

Well to answer your question mythtv has full rights as a group and I as a user have membership rights as well as full personal rights.

Last evening I setup an smb share, and added that to the frontend fstab, and further added that to mythfrontend, did an update of the db, and all worked fine, apart from it still complaining of not finding the host as stated earlier. All the frontends can see the server fine, and are being resolved by name perfectly. I use dnsmasq and dhcp. 

This seems to be some odd setting with the now mythvideo (Built in rather than add on, as it once was) But I cannot see anything obvious in the backend settings.

Regards Paul

---

### Post by tgm4883 on 2011-09-14
> **drifting said:**
> Hi Nick

Well to answer your question mythtv has full rights as a group and I as a user have membership rights as well as full personal rights.

Last evening I setup an smb share, and added that to the frontend fstab, and further added that to mythfrontend, did an update of the db, and all worked fine, apart from it still complaining of not finding the host as stated earlier. All the frontends can see the server fine, and are being resolved by name perfectly. I use dnsmasq and dhcp. 

This seems to be some odd setting with the now mythvideo (Built in rather than add on, as it once was) But I cannot see anything obvious in the backend settings.

Regards Paul

Mythvideo isn't built in yet, so I'm guessing that you are running the development version of MythTV (0.25). In that case, it's possible something is broken and needs fixed. 

Regarding the video's SG. The backend is the what needs access, which means the MythTV user. You may also want to verify you don't have any extra entries in the videos SG setup (this included blank entries)

---

### Post by drifting on 2011-09-28
> **tgm4883 said:**
> Mythvideo isn't built in yet, so I'm guessing that you are running the development version of MythTV (0.25). In that case, it's possible something is broken and needs fixed. 

Regarding the video's SG. The backend is the what needs access, which means the MythTV user. You may also want to verify you don't have any extra entries in the videos SG setup (this included blank entries)

I was convinced it was integrated, but as usual I am wrong :-) Have checked the backend and deleted the entry for the video, just in case there was a duff entry. Sadly still the same. Now I must admit that I had to change my DHCP server, as I was having issues from an earlier upgrade from 10.4. Have now installed DNSMasq, and for good measure on each frontend I have also added entries in the hosts for the server. 

I can play back any video that it has in the list fine, just cannot seem to update the list without error.

Regards Paul

---

### Post by nickrout on 2011-09-28
perhaps if you run the commands I suggested AND POST THE RESULTS we might get somewhere.

Also have you got any directories set up in mythvideo settings (ie in the front ends?)

---

### Post by drifting on 2011-10-08
> **nickrout said:**
> perhaps if you run the commands I suggested AND POST THE RESULTS we might get somewhere.

Also have you got any directories set up in mythvideo settings (ie in the front ends?)

Hi Nick

I did not reply to your post as I wanted to make sure that I was correct with the permissions. However I did nothing to the drive apart from a few updates to Ubuntu / Myth, now it scans the drive fine, and finds all the movies it could not before. However it still throws up the same error at the end, which seems not to affect anything?

I have checked the permissions on the drive that holds all the movies. Myth & Myself have full rights, for good measure I reset them. Still the same issue at the end.

Regards Paul

---

