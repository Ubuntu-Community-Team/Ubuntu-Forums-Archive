---
title: "No sound at start, only when i connect and disconnect headphones"
date: 2014-08-06
forum: Multimedia Software
---

### Post by carax007 on 2014-08-06
Hello community.

I hope someone can help me. And sorry my poor english.
When i installed ubuntu on my notebook i did it whit my headphones on, so now, when i start ubuntu at first there is no sound. Whar i have to do to get sound active again is connect and disconnect the headphones. Is not a big problem, but is an issue very distubant whit the time. 

Cheers,

Héctor.

---

### Post by Yellow Pasque on 2014-08-06
If you create a new user (make sure headphones are unlpugged when you log in as that user for the first time), do you have the same issue? If the new user does not have the issue, run this as your original user (with headphones unplugged):
```
rm -r ~/.config/pulse
pulseaudio -k
```

---

