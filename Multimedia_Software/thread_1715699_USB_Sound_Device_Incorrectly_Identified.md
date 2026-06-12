---
title: "USB Sound Device Incorrectly Identified"
date: 2011-03-27
forum: Multimedia Software
---

### Post by jeic on 2011-03-27
Hi All, to get started let me say I'm about a week into being a new Ubuntu user, and have had a mixed experience of things easy/hard to do. I am a software developer and Windows user almost exclusively, but have experience with some linux command line stuff so am not terribly nervous about the details. 

So the specific problem here is I have a USB sound card, the Turtle Beach Audio Advantage SRM. It is a 7.1 surround device with all sorts of inputs and outputs such as stereo mic and the 7.1 output in electrical and optical formats.

The problem I can't solve is when I plug the device in (to any of the USB ports) it comes up in Sound Preferences > Hardware as a "Audio Advantage Roadie" with 1 input. No outputs have been identified on it.

I mostly have no idea what I am doing, have been sniffing down the path of installing/reinstalling the alsa system using command line instructions/Ubuntu Software Centre etc. Some have suggested the problem may be quite simple, others have said I need to recompile the kernel. I have navigated to a few files that seem related, gleened from posts on similar topics I've seen but nothing is leaping out as obviously wrong. I'm not sure if the answer will be just manually editing a file to indicate the device has output, or if I will need to find/download/recompile a lot of things.

I believe I've learned that my device is built to a USB audio standard therefore should not need any special driver, but maybe that is not true.

I have seen the output of lsusb and it gives similar information ie "Audio Advantage Roadie" device name.

Anyway that is all I know/have tried, is there enough information for anyone to help with? FYI I am not looking to disable the internal audio system since both get used equally (laptop, USB device periodically attached)

Thanks,
JEIC

---

