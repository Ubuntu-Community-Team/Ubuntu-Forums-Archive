---
title: "(Natty) Connect only A2DP profile for bluetooth headset."
date: 2011-05-18
forum: Multimedia Software
---

### Post by zuker on 2011-05-18
I have a bluetooth headset with both support of HSP/HFP and A2DP. My goal is to connect this headset to my cell phone (over HSP/HFP) and to the PC (over A2DP) simultaneously, but ubuntu always connects both profiles.
I've tried to set following values in /etc/bluetooth/audio.conf:
```

[Gneral]
AutoConnect=false

[Headset]
HFP=false
HSP=false
MaxConnected=0
FastConnectable=false

```

But it has no effect.
Please advice how I can disable HSP/HFP connection?

---

### Post by zuker on 2011-05-24
Bump!

---

### Post by zuker on 2011-05-26
Adding following line to /etc/bluetooth/audio.conf in the [General] section solved my problem:
```

[General]
Disable=Headset

```

---

