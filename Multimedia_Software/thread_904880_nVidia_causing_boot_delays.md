---
title: "nVidia causing boot delays"
date: 2008-08-29
forum: Multimedia Software
---

### Post by CNLiberal on 2008-08-29
I'm running the latest MythBuntu and latest drivers.  I went from a DVI input (on a 22" LCD) to an SVideo-RCA converter into a 27" TV.  I put in the following into xorg.conf.

# TV Out Setup
    Option      "TVStandard" "NTSC-M"
    Option      "TVOutFormat" "COMPOSITE"
    Option      "UseEvents" "True"
    Option      "ConnectedMonitor" "TV"

I was using:

    Option     "TVOutFormat"  "SVideo"

and I was getting a Black and White picture.  I changed to "COMPOSITE" and now bootups are taking about 30 seconds longer.  I no longer have B&W picture, but this bootup is crazy.  Also, I can't open nvidia-settings anymore.  I tried running this command:

sudo nvidia-settings

and nothing shows up on the screen, and the terminal doesn't list any errors.  It just sits there.  Has anyone seen this?

Jim

---

