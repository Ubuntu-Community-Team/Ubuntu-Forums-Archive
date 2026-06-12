---
title: "set a new alsa config as default"
date: 2008-05-30
forum: Multimedia Software
---

### Post by legit on 2008-05-30
Okay so after a year of searching I finally found something that said how to switch my sound card channels.  So now I need to know how to set this as the default.

Can anyone explain how to do this?

heres my current asoundrc:

pcm.swap51 {
  @args.0 SLAVE
  @args.SLAVE {
    type string
    default "plughw:0,0"
  }
  type route
  slave {
    pcm $SLAVE
    channels 6
  }
  ttable {
    0.0= 1
    1.1= 1
    2.4= 1
    3.5= 1
    4.3= 1
    5.2= 1
  }
}

---

