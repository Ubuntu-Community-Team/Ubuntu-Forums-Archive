---
title: "[howto] ... run nvidia CUDA on Ubuntu 8.10 Intrepid"
date: 2009-02-05
forum: Multimedia Software
---

### Post by Krzysztof on 2009-02-05
This is for anybody interested in running nvidia CUDA on Ubuntu 8.10.

First, you have to assure that your nvidia card supports CUDA.
Check the list here:
[http://www.nvidia.com/object/cuda_learn_products.html]("http://www.nvidia.com/object/cuda_learn_products.html") 

Now since Ubuntu 8.10 comes with nvidia driver 177 we will make it all working for this particular driver. If you use another one you have to also download other versions of CUDA toolkit and CUDA SDK.

0. You must enable NVIDIA proprietary driver version 177 in 
System->Hardware Drivers. If you do this correctly, you will be able to open NVIDA X Server Settings. It is quite probable that you have already done this step before.

1. Go to [http://www.nvidia.com/object/cuda_get.html]("http://www.nvidia.com/object/cuda_get.html")
choose your platform (Linux-32) and Ubuntu 7.10. 

Download CUDA 2.0 toolkit: CUDA Toolkit for Ubuntu 7.10
and  CUDA SDK 2.0. Save them to say, ~/Desktop.

2. Open terminal and 
```

cd ~/Desktop
chmod u+x NVIDIA_CUDA_Toolkit_2.0_ubuntu7.10_x86.run
chmod u+x NVIDIA_CUDA_SDK_2.02.0807.1535_linux.run

```

3. Now we shall install the toolkit. You have to be root. The best option is just to confirm /usr/local/cuda as the destination directory.
```

sudo ./NVIDIA_CUDA_Toolkit_2.0_ubuntu7.10_x86.run

```
Then, we install the SDK with examples. You may do this in your home dir, so you don't have to be root any more:
```

./NVIDIA_CUDA_SDK_2.02.0807.1535_linux.run

```

4. You ahve been prompted to change $PATH and $LD_LIBRARY_PATH so we have to edit ~/.bashrc. Run
```

gedit ~/.bashrc

```
and paste the following code somewhere inside:
```

# extension for nvidia CUDA
PATH=$PATH:/usr/local/cuda/bin
export PATH
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib
export LD_LIBRARY_PATH

```

5. Now, we are almost done. The next thing you must do is to add gcc 4.1 and g++ 4.1 since CUDA uses them and Ubuntu 8.10 by default use gcc 4.3:
```

sudo apt-get install gcc-4.1 g++-4.1

``` 
Now we must set alternatives properly so, gcc 4.1 will be used by default. You may always switch back to 4.3.
```

sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.1 60 --slave /usr/bin/g++ g++ /usr/bin/g++-4.1 
 sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.3 40 --slave /usr/bin/g++ g++ /usr/bin/g++-4.3 

```

6. Finally you have to install all the stuff for OpenGL development:
```

sudo apt-get install mesa-common-dev freeglut3-dev glutg3-dev libglut3

```  
you will be prompted for other packages. Confirm them all.

**Now we are ready to compile the examples.** Go to the directory where you installed the SDK and 
```

make

```

If you haven't seen any errors (although you may see warnings) you are successful.
Let's try to run a demo:
```

./bin/linux/release/particles

```

**Enjoy!**

---

### Post by sse on 2009-02-14
Hi Krzysztof,

thanks for the guide!

I'm running 8.10 x86_64 with nvidia driver 180.29, CUDA toolkit 2.10 and SDK 2.10 (for 8.04).

I also had to install libxmu-dev and libc6-dev-i386 then everything worked fine.

Cheers

---

### Post by mallo on 2009-03-11
Hi,
I followed the steps proposed by both of you but I get an error on running the examples in SDK directory.

I'm running xubuntu 8.10 (64bit) and I used this procedure:
1) install nvidia driver 180s from synaptic
2) install nvidia toolbox and sdk using this guide
3) install the suggested libs in the reply too

The code in SDK compile but on running any example I get (e.g. devideQuery):


./deviceQuery: error while loading shared libraries: libcudart.so.2: cannot open shared object file: No such file or directory

The problem is libcudaart.so.2

I try to locate the libs and I don't have it. In this directories I have:

mallo release $  cd /usr/lib32/
mallo lib32 $  ls |grep cuda
libcuda.so
libcuda.so.1
libcuda.so.180.11
mallo lib32 $  cd /usr/lib
mallo lib $  ls |grep cuda
libcuda.so
libcuda.so.1
libcuda.so.180.11
libicudata.so.38
libicudata.so.38.1
mallo lib $  cd ..
mallo usr $  cd lib64
mallo lib64 $  ls |grep cuda
libcuda.so
libcuda.so.1
libcuda.so.180.11
libicudata.so.38
libicudata.so.38.1

Should I check some other things or should I install NVIDIA driver+CUDA from the website or rename some libs or something else?

Thanks in advance for the reply

---

### Post by zee on 2009-03-12
Hi there.
  Is it really neccessary to install the 32-bit version of the Cuda toolkit? I spotted a version for Ubuntu 8.04, is that not ok?

thanks in advance.

---

### Post by Krzysztof on 2009-03-12
> **zee said:**
> Hi there.
  Is it really neccessary to install the 32-bit version of the Cuda toolkit? I spotted a version for Ubuntu 8.04, is that not ok?

thanks in advance.

Honestly, I don't know I installed 32-bit version since I use 32-bit system only.

---

### Post by Krzysztof on 2009-03-12
> **mallo said:**
> Hi,
I followed the steps proposed by both of you but I get an error on running the examples in SDK directory.

I'm running xubuntu 8.10 (64bit) and I used this procedure:
1) install nvidia driver 180s from synaptic
2) install nvidia toolbox and sdk using this guide
3) install the suggested libs in the reply too

The code in SDK compile but on running any example I get (e.g. devideQuery):


./deviceQuery: error while loading shared libraries: libcudart.so.2: cannot open shared object file: No such file or directory

The problem is libcudaart.so.2

I try to locate the libs and I don't have it. In this directories I have:

mallo release $  cd /usr/lib32/
mallo lib32 $  ls |grep cuda
libcuda.so
libcuda.so.1
libcuda.so.180.11
mallo lib32 $  cd /usr/lib
mallo lib $  ls |grep cuda
libcuda.so
libcuda.so.1
libcuda.so.180.11
libicudata.so.38
libicudata.so.38.1
mallo lib $  cd ..
mallo usr $  cd lib64
mallo lib64 $  ls |grep cuda
libcuda.so
libcuda.so.1
libcuda.so.180.11
libicudata.so.38
libicudata.so.38.1

Should I check some other things or should I install NVIDIA driver+CUDA from the website or rename some libs or something else?

Thanks in advance for the reply

Hi, I can find libcudaart in my /usr/local/cuda/lib folder. That's the place where I installed CUDA. I think what you miss is an information for the system to look dynamically for libs also in this (/usr/local/cuda/lib) directory. 

You may set this path with 
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib
export LD_LIBRARY_PATH

or by adding 
/usr/local/cuda/lib 
to file: /etc/ld.so.conf and running ldconfig.

BTW. If you run ldconfig -p you will get information on all available dynamically linked libraries in the system.

---

### Post by mallo on 2009-03-12
Okay, I'm a stupid.

I hibernated the laptop and used the same terminal so I got two errors at the same time:
1) no update in the enviroment variables (source .bashrc)
2) no increment in NVIDIA version since I passed from 177 to 180 without reboot.

After the reboot everything runs and works perfectly!
I have a 64bit version so your steps are correct even for a 64bit architecture.

Please be free to insult me :\.

And in any case,

Thanks for everything,

Mauro

---

### Post by Krzysztof on 2009-03-18
> **mallo said:**
> 
I have a 64bit version so your steps are correct even for a 64bit architecture.


BTW. Mauro, do you feel the difference in performance with 64-bit Ubuntu when comparing to 32-bit version ?

K.

---

