---
title: "Problem with installing OpenCV and GPU"
date: 2013-02-21
forum: Multimedia Software
---

### Post by slsanthosh on 2013-02-21
Hello All,

I have Ubuntu 10.x installed in my PC.
On this I am trying to install OpenCV 2.4. I was able to Install OpenCV and was able to execute examples.
But when I tried to install GPU libraries and Make the OpenCV then I am seeing lot of issues.

Inorder to install GPU libraries, I was required to install 
libopencv-core2.3_2.3.1-11ubuntu2_i386
libopencv-core-dev_2.3.1-11ubuntu2_i386
libopencv-gpu2.3_2.3.1-11ubuntu2_i386
libopencv-gpu-dev_2.3.1-11ubuntu2_i386

But for installing these I was forced to install libc6_2.16-0ubuntu1_i386 (its earlier version was 2.13)

After successfull compiling these GPU libraries, when I tried to Configure and Make OpenCV, it is giving following error

The following packages have unmet dependencies:
  libc-dev-bin: Depends: libc6 (< 2.12) but 2.16-0ubuntu1 is to be installed
  libc6-dev: Depends: libc6 (= 2.11.1-0ubuntu7.12) but 2.16-0ubuntu1 is to be installed
  libc6-i686: PreDepends: libc6 (= 2.11.1-0ubuntu7.12) but 2.16-0ubuntu1 is to be installed
  libnih1: Depends: libc6 (< 2.12) but 2.16-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

But for GPU libraries,  libc6 should be >2.15

Can some one help me on this issue.

---

