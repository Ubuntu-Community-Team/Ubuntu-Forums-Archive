---
title: "compiling opal"
date: 2012-11-29
forum: Multimedia Software
---

### Post by volkerbradley on 2012-11-29
I would like to compile Ekiga 4.0 in Ubuntu 12.04. A dependency is opal >= 3.10.9.
 
I tried to compile this version of opal but received the following error messages: 

make[3]: Entering directory `/home/volker/Downloads/opal-3.10.9/plugins/video/H.263-1998'
[CC] h263-1998.cxx
h263-1998.cxx: In member function ‘virtual void H263_Base_EncoderContext::SetOption(const char*, const char*)’:
h263-1998.cxx:320:27: error: ‘CODEC_FLAG_H263P_UMV’ was not declared in this scope
h263-1998.cxx:322:28: error: ‘CODEC_FLAG_H263P_UMV’ was not declared in this scope
h263-1998.cxx:363:27: error: ‘CODEC_FLAG_H263P_SLICE_STRUCT’ was not declared in this scope
h263-1998.cxx:365:28: error: ‘CODEC_FLAG_H263P_SLICE_STRUCT’ was not declared in this scope
h263-1998.cxx:373:27: error: ‘CODEC_FLAG_H263P_AIV’ was not declared in this scope
h263-1998.cxx:375:28: error: ‘CODEC_FLAG_H263P_AIV’ was not declared in this scope
h263-1998.cxx: In member function ‘bool H263_Base_EncoderContext::OpenCodec()’:
h263-1998.cxx:455:3: error: ‘CODEC_FLAG_H263P_UMV’ was not declared in this scope
h263-1998.cxx:456:3: error: ‘CODEC_FLAG_OBMC’ was not declared in this scope
h263-1998.cxx:458:3: error: ‘CODEC_FLAG_H263P_SLICE_STRUCT’ was not declared in this scope
h263-1998.cxx:460:3: error: ‘CODEC_FLAG_H263P_AIV’ was not declared in this scope
h263-1998.cxx: In member function ‘virtual bool H263_Base_EncoderContext::EncodeFrames(const BYTE*, unsigned int&, BYTE*, unsigned int&, unsigned int&)’:
h263-1998.cxx:524:72: error: ‘FF_I_TYPE’ was not declared in this scope
h263-1998.cxx: In member function ‘virtual bool H263_RFC2190_EncoderContext::Init()’:
h263-1998.cxx:606:24: error: ‘CODEC_FLAG_H263P_UMV’ was not declared in this scope
h263-1998.cxx:611:24: error: ‘CODEC_FLAG_H263P_AIV’ was not declared in this scope
h263-1998.cxx:612:24: error: ‘CODEC_FLAG_H263P_SLICE_STRUCT’ was not declared in this scope
make[3]: *** [/home/volker/Downloads/opal-3.10.9/plugins/../lib_linux_x86_64/plugins/h263_ffmpeg/h263-1998.o] Error 1
make[3]: Leaving directory `/home/volker/Downloads/opal-3.10.9/plugins/video/H.263-1998'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/volker/Downloads/opal-3.10.9/plugins'
make[1]: *** [subdirs] Error 2
make[1]: Leaving directory `/home/volker/Downloads/opal-3.10.9'
make: *** [opt] Error 2

Is there a solution for this?

---

### Post by cIdde on 2013-03-09
Well, opal should be there in the right version. Maybe you forgot to install the development package: libopal-dev which you will need when compiling something that uses opal?

But I also tried to build ekiga (4.0.1) and configure complains that it cannot find gtk+:

```
configure: error: Package requirements (gtk+-2.0 >= 2.20.0 gnome-icon-theme >= 3.0.0) were not met
```

When I look in the package list, I have gtk3 installed (libgtk-3-dev). libgtk-2 does not seem to be available. Anyone any idea how to solve that? I realld do not want to compile gtk2 on my system just for that...

---

### Post by mc4man on 2013-03-09
> **cIdde said:**
> Well, opal should be there in the right version. Maybe you forgot to install the development package: libopal-dev which you will need when compiling something that uses opal?

But I also tried to build ekiga (4.0.1) and configure complains that it cannot find gtk+:

```
configure: error: Package requirements (gtk+-2.0 >= 2.20.0 gnome-icon-theme >= 3.0.0) were not met
```

When I look in the package list, I have gtk3 installed (libgtk-3-dev). libgtk-2 does not seem to be available. Anyone any idea how to solve that? I realld do not want to compile gtk2 on my system just for that...

whether you can compile ekiga no clue, haven't tried in many releases. As far as gtk2 - 

libgtk2.0-dev

---

### Post by andrew.46 on 2013-03-09
I am not such a big fan of this method but a shotgun approach is often to use:

```
sudo apt-get build-dep ekiga
```

The shortcoming is that often this drags in some non-essential libraries, wrong versions etc, but on Ubuntu it often makes a good starting point...

---

