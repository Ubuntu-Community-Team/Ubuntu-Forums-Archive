---
title: "Network Attached Storage and Mythtv"
date: 2012-07-11
forum: Mythbuntu
---

### Post by se99paj on 2012-07-11
So I've been having a thought about my existing MythTV setup and thought it might be time to do some upgrades to improve performance.

At the moment I have a combined frontend/backend, I'd like to split the frontend and backend across two PC's and use low energy components to try and reduce the costs.

I had a thought that I could use a low power NAS server to store all my data instead of dropping more HDD into the backend. The reason behind this is so that I could keep the NAS on 24x7, and the backend would only ever need to be turned on for recording and transcoding. If I wanted to watch a recording the frontend would be able to run the files from the NAS, is this possible?

Does the backend need to communicate with the backend to watch recordings or can it just run the files from a network drive?

Also are there any other issues that I should be thinking about?

---

### Post by nickrout on 2012-07-11
> **se99paj said:**
> So I've been having a thought about my existing MythTV setup and thought it might be time to do some upgrades to improve performance.

At the moment I have a combined frontend/backend, I'd like to split the frontend and backend across two PC's and use low energy components to try and reduce the costs.

I had a thought that I could use a low power NAS server to store all my data instead of dropping more HDD into the backend. The reason behind this is so that I could keep the NAS on 24x7, and the backend would only ever need to be turned on for recording and transcoding. If I wanted to watch a recording the frontend would be able to run the files from the NAS, is this possible?

Does the backend need to communicate with the backend to watch recordings or can it just run the files from a network drive?

Also are there any other issues that I should be thinking about?

No, you need the backend on to use a frontend.

---

