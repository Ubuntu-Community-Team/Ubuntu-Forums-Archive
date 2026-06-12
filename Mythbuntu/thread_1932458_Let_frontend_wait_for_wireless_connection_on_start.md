---
title: "Let frontend wait for wireless connection on startup"
date: 2012-02-27
forum: Mythbuntu
---

### Post by joexner on 2012-02-27
Hi all,

I've got a frontend/backend running on Mythbuntu stable (0.24.whatever). The frontend uses wi-fi 802.11n (5 ghz) to connect to the backend machine, and playback is good, even on hi-def sources.

However, when the frontend starts up it always fails until the network manager connects. I have to cancel out of the setup GUI and wait until the wireless connects (usually before I can even finish cancelling). Is there a way to make mythfrontend wait until the network is connected before starting up?

Thanks,
Jon

---

### Post by nickrout on 2012-02-27
the startup script is /usr/bin/mythfrontend. Put a test at the start of it.

---

