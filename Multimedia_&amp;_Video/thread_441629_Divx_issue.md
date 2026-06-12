---
title: "Divx issue"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by Dayylin on 2007-05-12
Hi,

I started the install of divx 6.11. At the bottom of it, I get a error saying that the directory isn't found. The error is below in bold. Any ideas?


dayylin@********:~/Desktop/downloads/divx$ sudo ./install.sh

Do you accept the terms of this agreement? Please type yes or no.
yes
Proceeding with installation
Archive:  contents.dat
   creating: /tmp/.divx/include/
   creating: /tmp/.divx/include/common/
  inflating: /tmp/.divx/include/common/DivXPortable.h  
  inflating: /tmp/.divx/include/common/FourCC.h  
  inflating: /tmp/.divx/include/common/FourCCs.h  
  inflating: /tmp/.divx/include/common/FormatInfo.h  
   creating: /tmp/.divx/include/encoder/
  inflating: /tmp/.divx/include/encoder/Settings.h  
  inflating: /tmp/.divx/include/encoder/EncoderCallback.h  
  inflating: /tmp/.divx/include/encoder/FrameResult.h  
  inflating: /tmp/.divx/include/encoder/FrameOutput.h  
  inflating: /tmp/.divx/include/encoder/EncoderInterface.h  
  inflating: /tmp/.divx/include/encoder/FrameInput.h  
  inflating: /tmp/.divx/include/encoder/FeedbackInterface.h  
  inflating: /tmp/.divx/include/encoder/Cli.h  
  inflating: /tmp/.divx/include/encoder/DivXException.h  
   creating: /tmp/.divx/include/decoder/
  inflating: /tmp/.divx/include/decoder/LibQDec.h  
   creating: /tmp/.divx/lib/
  inflating: /tmp/.divx/lib/libdivx.so  
**cp: cannot stat `/tmp/.divx/include/*.h': No such file or directory**

---

