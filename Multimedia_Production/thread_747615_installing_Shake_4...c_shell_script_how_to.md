---
title: "installing Shake 4...c shell script how to"
date: 2008-04-06
forum: Multimedia Production
---

### Post by homy06 on 2008-04-06
[https://answers.launchpad.net/ubuntu/+question/7185](https://answers.launchpad.net/ubuntu/+question/7185)

I'm installing shake 4 on gutsy and I'm almost done, i just need help with this last portion. The link above states that the permissions for two files need to be changed first. I was wondering how to do that, apparently its done with a c shell script. 

I installed csh and tcsh. I just can't translate t this last portion 

any help is very much appreciated and I'm sure this thread would become popular if solved. thanks so much


```
#!/bin/csh -f

#
# set env var, NR_SHAKE_LOCATION if not set
#
#!/bin/csh -f

#
# set env var, NR_SHAKE_LOCATION if not set
#
if ${?NR_SHAKE_LOCATION} == 0 then
  pushd `dirname $0` >& /dev/null
  setenv NR_SHAKE_LOCATION `dirname ${cwd}`;
  popd >& /dev/null
endif

#
# set env var, LD_LIBRARYN32_PATH
#
if ${?LD_LIBRARYN32_PATH} then
  setenv LD_LIBRARYN32_PATH ${NR_SHAKE_LOCATION}/lib:${LD_LIBRARYN32_PATH};
else
  setenv LD_LIBRARYN32_PATH ${NR_SHAKE_LOCATION}/lib;
endif

#
# set env var, LD_LIBRARY_PATH
#
if ${?LD_LIBRARY_PATH} then
  setenv LD_LIBRARY_PATH /usr/lib:${NR_SHAKE_LOCATION}/lib:${NR_SHAKE_LOCATION}/lib/mesa:${LD_LIBRARY_PATH};
else
  setenv LD_LIBRARY_PATH /usr/lib:${NR_SHAKE_LOCATION}/lib:${NR_SHAKE_LOCATION}/lib/mesa;
endif

#
# launch shake
#
exec ${NR_SHAKE_LOCATION}/bin/shkx.exe $argv:q

#echo NR_SHAKE_LOCATION = ${NR_SHAKE_LOCATION};
#echo LD_LIBRARYN32_PATH = ${LD_LIBRARYN32_PATH};
#echo LD_LIBRARY_PATH = ${LD_LIBRARY_PATH};

There is also this script too...

#!/bin/csh -f

#
# set env var, NR_SHAKE_LOCATION if not set
#
#!/bin/csh -f

#
# set env var, NR_SHAKE_LOCATION if not set
#
if ${?NR_SHAKE_LOCATION} == 0 then
  pushd `dirname $0` >& /dev/null
  setenv NR_SHAKE_LOCATION `dirname ${cwd}`;
  popd >& /dev/null
endif

#
# set env var, LD_LIBRARYN32_PATH
#
if ${?LD_LIBRARYN32_PATH} then
  setenv LD_LIBRARYN32_PATH ${NR_SHAKE_LOCATION}/lib:${LD_LIBRARYN32_PATH};
else
  setenv LD_LIBRARYN32_PATH ${NR_SHAKE_LOCATION}/lib;
endif

#
# set env var, LD_LIBRARY_PATH
#
if ${?LD_LIBRARY_PATH} then
  setenv LD_LIBRARY_PATH /usr/lib:${NR_SHAKE_LOCATION}/lib:${NR_SHAKE_LOCATION}/lib/mesa:${LD_LIBRARY_PATH};
else
  setenv LD_LIBRARY_PATH /usr/lib:${NR_SHAKE_LOCATION}/lib:${NR_SHAKE_LOCATION}/lib/mesa;
endif

#
# launch tshake
#
exec ${NR_SHAKE_LOCATION}/bin/tshkx.exe $argv:q

#echo NR_SHAKE_LOCATION = ${NR_SHAKE_LOCATION};
#echo LD_LIBRARYN32_PATH = ${LD_LIBRARYN32_PATH};
#echo LD_LIBRARY_PATH = ${LD_LIBRARY_PATH}; 
```



I also followed this guy's instructions 
[http://ubuntuforums.org/showthread.php?t=615277](http://ubuntuforums.org/showthread.php?t=615277)

but it continues to deny me permission and I couldn't find the /var/flexlm  folder he mentioned.

---

### Post by homy06 on 2008-04-06
solved well one way dunno if its the best or what

following the second link's instructions

chmod 755 * /usr/apple/shake-4..../bin

that changes permissions

then i just csh shake and it opens shake for me.

but you have to be in the folder to do so, you can't just open terminal and type csh shake.

and the script above should be what you see in the shake file


the only thing left to do is figure out how to make it launchable from cairo dock..

anyone?

---

