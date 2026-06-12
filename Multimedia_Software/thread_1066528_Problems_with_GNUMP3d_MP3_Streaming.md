---
title: "Problems with GNUMP3d MP3 Streaming"
date: 2009-02-10
forum: Multimedia Software
---

### Post by alex2325 on 2009-02-10
Hello,

I successfully installed and can access GNUMP3d MP3 streaming on my home LAN.  However, I can't seem to create a Custom Playlist.  When I go there in the web interface (and I have tried different themes for this as well) all I have is the Clear All and Play buttons.  There is no music listed.  I can see my music under other options on this web interface, but not on this particular page.  Any help would be greatly appreciated.  I want to create a custom playlist.  Thanks.

---

### Post by sonicb00m on 2009-02-11
> **alex2325 said:**
> Hello,

I successfully installed and can access GNUMP3d MP3 streaming on my home LAN.  However, I can't seem to create a Custom Playlist.  When I go there in the web interface (and I have tried different themes for this as well) all I have is the Clear All and Play buttons.  There is no music listed.  I can see my music under other options on this web interface, but not on this particular page.  Any help would be greatly appreciated.  I want to create a custom playlist.  Thanks.

I can't directly answer your question but maybe you should look at icecast instead?

I used to use Gnump3d but it's very un-secure. For some mad reason they took away the password box to stop people idly browsing your media list through the web. When I confronted the author about this his reply was "it's a false sense of security since the audio can still be accessed". He further admitted that the audio could only be accessed if you knew what you were looking for, i.e. the filename on the server! I had to dump the software because firewalling on a dynamic client ip proved impossible.

If you are using it locally I guess it's a great piece of software but I noticed it was dropped from the repo's.

I know the software stopped development so it's likely there are still bugs and that's why you are having trouble.

---

