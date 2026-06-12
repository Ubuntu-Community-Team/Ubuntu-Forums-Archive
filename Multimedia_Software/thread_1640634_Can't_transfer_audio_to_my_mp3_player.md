---
title: "Can't transfer audio to my mp3 player"
date: 2010-12-08
forum: Multimedia Software
---

### Post by thync on 2010-12-08
I cannot transfer mp3/wav/ogg files to my Samsung YP-S3 media player from any of Rhythmbox/Amarok/Banshee. I was able to in Lucid but not since going Maverick.

It should be a simple fix as both Banshee and Rhythmbox give similar error messages (see below) while Amarok just hangs on 10% transferred.

Rhythmbox: 

Unable to send file to MTP device: PTP Layer error 200c: send_file_object_info(): Could not send object info.

Banshee:

LIBMTP_Send_Track_From_File_Descriptor(): subcall to LIBMTP_Send_Track_From_File_Descriptor failed

Nautilus (dragging and dropping in shell):

Error writing file: -1: Unspecified error

I have libmtp8, python-pymtp & mtp-tools installed as well as the latest gstreamer good/bad/ugly.

Any help would be appreciated.

---

