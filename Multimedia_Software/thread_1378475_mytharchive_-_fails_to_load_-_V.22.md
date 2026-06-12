---
title: "mytharchive - fails to load - V.22"
date: 2010-01-11
forum: Multimedia Software
---

### Post by wooddealer on 2010-01-11
I recently upgraded my MythTV combined frontend/backend machine from MythTV version 0.21 to 0.22.  Prior to doing the upgrade mytharchive worked wonderfully, now it won't even load.  The OSD says something to the effect of, "mytharchive failed to load for some reason."  Below is the output from the log file.  I've googled for some time now and can't track down what's wrong.  Anybody want to offer hints?

```

2010-01-08 20:59:51.917 MythPlugin::init() dlerror: libraw1394.so.8: cannot open shared object file: No such file or directory.
2010-01-08 20:59:51.917 Unable to initialize plugin 'mytharchive'.
2010-01-08 20:59:52.035 MMUnix::AddDevice() Error: failed to stat /dev/bdi,
                        eno: No such file or directory (2)
2010-01-08 20:59:52.037 MMUnix::AddDevice() Error: failed to stat /dev/power,
                        eno: No such file or directory (2)
2010-01-08 20:59:52.043 MMUnix::AddDevice() Error: failed to stat /dev/trace,
                        eno: No such file or directory (2)
2010-01-08 20:59:52.055 MonitorRegisterExtensions(0x100, gif,jpg,png)


```

I currently have libraw1394-11 installed, and can't figure out how to make mytharchive happy with that version.  Thanks in advance.

---

### Post by wooddealer on 2010-01-13
I have managed to correct this problem by uninstalling and reinstalling mytharchive using "apt-get" instead of "synaptic package manager" (which I had tried originally).  Hope this helps someone.

---

