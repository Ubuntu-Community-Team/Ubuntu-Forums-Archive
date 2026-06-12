---
title: "error while unpacking hydrogen .9.5"
date: 2011-07-04
forum: Multimedia Software
---

### Post by stephenstop on 2011-07-04
```

```=================================================================
 Hydrogen build script

/bin/sh: svnversion: not found
 Revision: 
 Platform: linux2
 Release build
 Prefix: /usr/local
 Destdir: 
=================================================================
Feature Overview:

      lash: disabled
      oss: enabled
      alsa: enabled
      jack: enabled
libarchive: disabled
 portaudio: disabled
  portmidi: disabled

=================================================================

/bin/sh: svnversion: not found
EnvironmentError: No tool named 'qt4': not a Zip file:
  File "/home/owner/hydrogen-0.9.5/Sconstruct", line 528:
    libhyd = get_hydrogen_lib( opts )
  File "/home/owner/hydrogen-0.9.5/Sconstruct", line 187:
    env = Environment(options = opts , tools=['default','qt4'], toolpath=[qt4ToolLocation], ENV=os.environ, CPPPATH = includes, CPPFLAGS = cppflags, CCFLAGS = "", LINKFLAGS=ldflags )
  File "/usr/lib/scons/SCons/Environment.py", line 1005:
    apply_tools(self, tools, toolpath)
  File "/usr/lib/scons/SCons/Environment.py", line 107:
    env.Tool(tool)
  File "/usr/lib/scons/SCons/Environment.py", line 1703:
    tool = apply(SCons.Tool.Tool, (tool, toolpath), kw)
  File "/usr/lib/scons/SCons/Tool/__init__.py", line 95:
    module = self._tool_module()
  File "/usr/lib/scons/SCons/Tool/__init__.py", line 155:
    raise SCons.Errors.EnvironmentError, m
owner@owner-laptop:~/hydrogen-0.9.5$

---

