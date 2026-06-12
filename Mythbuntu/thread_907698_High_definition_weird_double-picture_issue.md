---
title: "High definition weird double-picture issue"
date: 2008-09-01
forum: Mythbuntu
---

### Post by dark_ixion on 2008-09-01
I've already read the double-picture problem someone else reported, but this one is actually different.

I've got Mythbuntu 8.04 installed and all standard-definition content looks fine, but when I switch over to BBC HD it is okay for a couple seconds then I suddenly get a smaller version of the picture in the top-left-hand corner, on top of the larger picture.  They are the same programme.  I've checked that picture-in-picture isn't enabled too.

Does anyone know what might be causing this?  Could it be a MythTV configuration problem?  Or nVidia driver settings?

I've attached a screenshot.  Unfortunately I could only get it from a VNC session, but it shows the problem adequately.

Thanks

Thom

---

### Post by ian dobson on 2008-09-02
Hi,

I'm seeing exactly the same problem with BBC HD, I also have a nVidia card.

For me it's not a major problem as I only have an old Analog TV at the moment.

Regards
Ian Dobson

---

### Post by dark_ixion on 2008-09-02
See, I don't know if it's a display driver issue (i.e. nVidia settings etc) or something MythTV is doing to images higher than a certain resolution.  I've played around with the "TV Playback" settings, or whatever it's called, and made sure there's a proper rule which covers resolutions of H1920 and V1080 but it hasn't improved things.

I've been through the nVidia config and can't see any options which would remedy this.

---

### Post by Neon Dusk on 2008-09-02
I think this is a MHEG [bug](http://svn.mythtv.org/trac/ticket/5606).

Disabling 'Interactive TV' should fix it

---

### Post by dark_ixion on 2008-09-02
> **Neon Dusk said:**
> I think this is a MHEG [bug](http://svn.mythtv.org/trac/ticket/5606).

Disabling 'Interactive TV' should fix it

Cool, I'll give that a go.  I don't actually use MHEG on the MythTV box anyway, only on the actual digital channels on the TV unit itself.

Thanks.

---

### Post by dark_ixion on 2008-09-02
Yep, that worked!  Thanks for your help.

---

