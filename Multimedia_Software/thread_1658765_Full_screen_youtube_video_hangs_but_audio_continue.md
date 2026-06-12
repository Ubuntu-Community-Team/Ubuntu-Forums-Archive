---
title: "Full screen youtube video hangs but audio continues"
date: 2011-01-03
forum: Multimedia Software
---

### Post by zaphod777 on 2011-01-03
When playing a Full screen youtube video hangs but audio continues. I have tested in both firefox and Chrome.

Anyone else having this issue or know which project I should report a bug under?

---

### Post by lovinglinux on 2011-01-03
Get [Flash-Aid 2.0]("http://www.webgapps.org/addons/flash-aid") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should fix your problems. If you still get that issue after running Flash-Aid, then go to the extension Help tab, click the "Generate Report" button and send me the results so I can analyze your situation.

---

### Post by zaphod777 on 2011-01-03
> **lovinglinux said:**
> Get [Flash-Aid 2.0]("http://www.webgapps.org/addons/flash-aid") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should fix your problems. If you still get that issue after running Flash-Aid, then go to the extension Help tab, click the "Generate Report" button and send me the results so I can analyze your situation.

Thanks that worked like a charm. It looks like it removed the x32 Flash Ubuntu installed by default and installed the latest x64 version. I guess the x64 version has gotten better. On my last system it was kind of buggy and the x32 version worked better. Nice to see x64 version getting some love.

---

### Post by lovinglinux on 2011-01-03
> **zaphod777 said:**
> Thanks that worked like a charm. It looks like it removed the x32 Flash Ubuntu installed by default and installed the latest x64 version.

Yes, by default it installs the 64bit preview, except on Hardy, because of crashes.

> **zaphod777 said:**
>  I guess the x64 version has gotten better. On my last system it was kind of buggy and the x32 version worked better. Nice to see x64 version getting some love.

This could happen or Adobe could stop providing the 64bit again. If that happens, use the extension "Expert Mode" to install the version from the repositories.

---

### Post by ajblue98 on 2011-01-12
W00t!  I just installed Maverick Meerkat on my HP, and this fixed my Flash woes instantly.  Thanks to zaphod777 and lovinglinux!

—AJBlue98

---

### Post by lovinglinux on 2011-01-13
> **ajblue98 said:**
> W00t!  I just installed Maverick Meerkat on my HP, and this fixed my Flash woes instantly.  Thanks to zaphod777 and lovinglinux!

—AJBlue98

You are welcome.

---

### Post by lupo1939 on 2011-01-14
I installed Flashaid 2.0 and it disabled Firefox.  Had to remove and reinstall Firefox an flash plugin to recover the function.

---

### Post by lovinglinux on 2011-01-14
> **lupo1939 said:**
> I installed Flashaid 2.0 and it disabled Firefox.  Had to remove and reinstall Firefox an flash plugin to recover the function.

If Firefox cannot start after installing an extension, then start it in safe-mode:

```
firefox -safe-mode
```

When in safe mode you can disable the problematic extension. So there is no need for re-installing Firefox.

When you say Flash-Aid disabled Firefox, what do you mean? You couldn't start Firefox, it started but did not respond or something else?

---

### Post by fugalaya on 2011-04-02
Thanks!  This worked for me.

---

### Post by myshanks on 2011-04-04
Thanks buddy, it worked for me after installing your solution

shanks

---

### Post by myshanks on 2011-04-04
> **lovinglinux said:**
> Get [Flash-Aid 2.0]("http://www.webgapps.org/addons/flash-aid") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should fix your problems. If you still get that issue after running Flash-Aid, then go to the extension Help tab, click the "Generate Report" button and send me the results so I can analyze your situation.

Thanks buddy, it worked for my after installing your solution

shanks

---

### Post by lovinglinux on 2011-04-04
> **myshanks said:**
> Thanks buddy, it worked for my after installing your solution

shanks

You are welcome.

---

