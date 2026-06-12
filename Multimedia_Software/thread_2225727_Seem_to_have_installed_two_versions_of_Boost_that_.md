---
title: "Seem to have installed two versions of Boost that conflict...CMake problems..."
date: 2014-05-22
forum: Multimedia Software
---

### Post by chris231 on 2014-05-22
I followed these steps to install boost by source. I was trying to compile it only in a directory so that I could point a single application to it. I accidentally installed it to the system, and now it's breaking other apps when I compile them that apparently don't work with version 1.55. These apps are compiled using CMake.

Original version of Boost on my system:
1.46.1

I followed these steps to install Boost by source (except that I've currently removed the local.conf file:
[https://coderwall.com/p/0atfug](https://coderwall.com/p/0atfug)
--This installed Boost 1.55 by source.

Here's the error it gives me in an application that bombs when it apparently finds version 1.55. The app uses Cuda, but the thing that changed was Boost.
```

/usr/local/include/boost/assert.hpp:102:47: error: &#8216;noinline&#8217; was not declared in this scope
CMake Error at TestBuild_dax_cuda_cont_generated_TestBuild_dax_cuda_cont_DeviceAdapterCuda.cu.o.cmake:256 (message):
Error generating file
/home/datahead/code/DaxBuild/dax/cuda/cont/CMakeFiles/TestBuild_dax_cuda_cont.dir/__/__/__/__/DaxBuild/dax/cuda/cont/testing/./TestBuild_dax_cuda_cont_generated_TestBuild_dax_cuda_cont_DeviceAdapterCuda.cu.o

```

**I think that the copy in /usr/local/include is the version from source.**
If I can just get it to read from /usr/include I think it may very well work, which will let me continue doing some work for now.
Ultimately, I want to purge the entire /usr/local/include installation and only use Boost 1.55 from that one directory for that one app.

It seems likely I need to tell CMake to point to the proper lib and include directory. I'm not sure how to do this properly or if I need to do additional changes.

This is my Linux distro:
```

datahead@datahead-G750JW:/usr/include$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 12.04.4 LTS
Release: 12.04
Codename: precise

```


=========================================================================

I just tried this on suggestion from a friend.
I put this in the project's CMakeLists.txt file:

cmake_minimum_required(VERSION 2.8.7)

[B]set(CMAKE_INCLUDE_PATH "/usr/include")
set(CMAKE_LIBRARY_PATH "/usr/lib")[/B]

I then ran cmake-gui again and make, per [http://www.daxtoolkit.org/index.php/Building_the_Dax_Toolkit:](http://www.daxtoolkit.org/index.php/Building_the_Dax_Toolkit:)
```

cd DaxBuild && cmake-gui ../DaxToolkit
make

```

But I get the same error:
```

/usr/local/include/boost/assert.hpp:102:47: error: &#8216;noinline&#8217; was not declared in this scope
CMake Error at TestBuild_dax_cuda_cont_generated_TestBuild_dax_cuda_cont_DeviceAdapterCuda.cu.o.cmake:256 (message):
  Error generating file
  /home/datahead/code/DaxBuild/dax/cuda/cont/CMakeFiles/TestBuild_dax_cuda_cont.dir/__/__/__/__/DaxBuild/dax/cuda/cont/testing/./TestBuild_dax_cuda_cont_generated_TestBuild_dax_cuda_cont_DeviceAdapterCuda.cu.o

```

---

### Post by steeldriver on 2014-05-22
Have you tried running cmake for the application you're compiling with the -LH or -LAH switches to see if there's a variable to define the boost location?

```

cmake -LAH .. | grep BOOST

```

Then you should be able to do something like

```

cmake -DWITH_BOOST=/usr ..

```

---

### Post by chris231 on 2014-05-22
```

datahead@datahead-G750JW:~/code/DaxToolkit$ cmake -LAH | grep -i boost
-- Boost version: 1.46.1
-- Boost version: 1.46.1
Boost_INCLUDE_DIR:PATH=/usr/include

```

Changed CMakeLists.txt's start:
```

cmake_minimum_required(VERSION 2.8.7)

set(CMAKE_INCLUDE_PATH "/usr/include")
set(CMAKE_LIBRARY_PATH "/usr/lib")
set(Boost_INCLUDE_DIR:PATH "/usr/include")

```

I did cmake-gui and make as discussed in the edited post above.  It then gave the same error:
```

/usr/local/include/boost/assert.hpp:102:47: error: &#8216;noinline&#8217; was not declared in this scope
CMake Error at TestBuild_dax_cuda_cont_generated_TestBuild_dax_cuda_cont_DeviceAdapterCuda.cu.o.cmake:256 (message):
  Error generating file
  /home/datahead/code/DaxBuild/dax/cuda/cont/CMakeFiles/TestBuild_dax_cuda_cont.dir/__/__/__/__/DaxBuild/dax/cuda/cont/testing/./TestBuild_dax_cuda_cont_generated_TestBuild_dax_cuda_cont_DeviceAdapterCuda.cu.o


```

---

