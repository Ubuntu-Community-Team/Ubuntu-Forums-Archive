---
title: "Whill this setup work? i.e. advice!"
date: 2009-04-01
forum: Mythbuntu
---

### Post by djbon2112 on 2009-04-01
I'm planning to setup a server/HTPC system at home using Mythbuntu, but I think I'm confused on the way the backend/frontend system work. I was wondering if someone could clarify for me.

I will be playing primarily 720p video (x264, Matroska container). I was planning to set up a relatively powerful backend server to do the decoding/transcoding so I could use something like an Intel Atom (or other microITX) system as the frontend for completely silent performance. After reading about VDPAU I was also considering putting a GPU in the server to assist in the decoding.

Would this setup work? Am I horribly confused as to how the MythTV backend/frontend system is supposed to work? Would the GPU be used for transcoding the videos, or not at all? Any help would be appreciated!

---

### Post by nickrout on 2009-04-01
No the GPU is not used for transcoding. A standalone backend has no use for a video card other than for installing and maintenance.

I recommend getting a frontend that will actually play the files you have. Something with a VDPAU capable graphics card would be ideal, it can still use a atom or other low power cpu.

---

### Post by AboveTheLogic on 2009-04-01
What will your video sources be? Are you going to install a tuner? You didn't mention a tuner although I guess it can be assumed that you will. If you are not going to use a tuner, then I don't think you reallllly need to setup a mythtv backend/frontend... rather just a media player that will grab your media files from a network share.

Anyways, I second what nickrout said. A powerful video card isn't necessary on a machine that won't have a frontend.

---

### Post by djbon2112 on 2009-04-01
Alright. I was hoping I'd basically be able to decode/transcode the HD video on the powerful backend server and stream it to a silent, fanless, low-power micro-HTPC, but I guess that's not the way that system works. Oh well, that's my answer. Thanks!

---

### Post by uncle hammy on 2009-04-02
Well, that is how the system works (i.e. backend stores the files, and then streams them to the frontend).  However, any frontend will have to have the ability to play what ever is being streamed to it.  You can't build a backend that will remove the entire load off the frontend.

---

### Post by nickrout on 2009-04-02
> **uncle hammy said:**
> Well, that is how the system works (i.e. backend stores the files, and then streams them to the frontend).  However, any frontend will have to have the ability to play what ever is being streamed to it.  You can't build a backend that will remove the entire load off the frontend.

If your frontend cannot play what your backend is offering, then with mythtv you have two options.

1. get a better frontend

2. transcode to an easier (and probably lower quality) format.

The backend is not able to transcode on the fly, so option 2 means doing it in advance.

Alternatively you could try a uPnP server like FUPPES on the backend, which is able to transcode on the fly. You will need grunt on the backend to do it though.

Frankly putting an nVidia 8/9 series vdpau capable graphics card in your atom motherboard (ie option 1 above) is IMHO the best solution.

---

