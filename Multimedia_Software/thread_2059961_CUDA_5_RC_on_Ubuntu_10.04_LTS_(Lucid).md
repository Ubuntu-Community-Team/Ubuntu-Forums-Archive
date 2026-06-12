---
title: "CUDA 5 RC on Ubuntu 10.04 LTS (Lucid)?"
date: 2012-09-19
forum: Multimedia Software
---

### Post by feneks on 2012-09-19
Hello!

I'd like to run the release candidate of [ CUDA-toolkits 5.0 ]("http://developer.nvidia.com/cuda/cuda-toolkit") on Ubuntu 10.04 (Lucid). [Documentation ]("http://developer.download.nvidia.com/compute/cuda/5_0/rc/docs/CUDA_Toolkit_Release_Notes_And_Errata.txt") of Nvidia states Lucid to be supported but it needs glibc version 2.12.1 und gcc version 4.4.5 .

The problem is my Lucid only has glibc 2.11.1 and gcc 4.4.3

Has anybody already experience with CUDA 5.0 RC on Lucid and can give some lead?

feneks

[http://developer.download.nvidia.com/compute/cuda/5_0/rc/docs/CUDA_Toolkit_Release_Notes_And_Errata.txt]("http://developer.download.nvidia.com/compute/cuda/5_0/rc/docs/CUDA_Toolkit_Release_Notes_And_Errata.txt")

---

### Post by BicyclerBoy on 2012-09-19
Can't help with recent cuda install but..

You can upgrade the lucid toolchain to 4.5 - 4.7 using this ppa:
[https://launchpad.net/~ubuntu-toolchain-r/+archive/test?field.series_filter=lucid](https://launchpad.net/~ubuntu-toolchain-r/+archive/test?field.series_filter=lucid)

Need to do some tweaking with alternatives etc to get the later toolchain to be default.
I have been using gcc4.6 on lucid to compile mkvtoolnix, MythTV etc..

I think there are later glibc (libglib2.xx-dev) available..

There are warnings about compiling/using kernel modules when using different toolchain version to the kernel..

---

