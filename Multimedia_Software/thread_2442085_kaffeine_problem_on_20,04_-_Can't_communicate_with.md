---
title: "kaffeine problem on 20,04 - Can't communicate with kded_kcookiejar"
date: 2020-04-29
forum: Multimedia Software
---

### Post by interglossa on 2020-04-29
I just installed 20.04 LTS and then installed kaffeine via command-line apt.  When I try to "Update Scan Data over Internet", I get

  kdeinit5: Got EXEC_NEW '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/http.so' from launcher.
  kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/http.so'
  kf5.kio.kio_http: Can't communicate with kded_kcookiejar!
  kdeinit5: PID 16279 terminated.

Should I have installed anything else?

Update: you don't do it this way. You use w_scan to create a list of frequencies and then convert the v5 output to v3 for kaffeine and then poke it in with the 'Edit scan data' button in 'Configure'.

---

