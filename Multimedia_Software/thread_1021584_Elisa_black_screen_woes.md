---
title: "Elisa black screen woes"
date: 2008-12-25
forum: Multimedia Software
---

### Post by Ekeluo on 2008-12-25
Well, hello again (what? I haven't posted since Obama started campaigning:mrgreen:).

What brings me here then? As the title boldly claims, elisa refuses to behave like it used to on hardy (v0.3.5 then, v0.5.22 now [ppa dev repos]). I had 0.5.9 since but it utterly refused to work. Double click, splash scr, then black full screen; no response to any input except Alt+F4, which promptly sent it back to wherever it came from.

Upgraded her to 0.5.22 some minutes ago, same behaviour(B***h!!!!). Except she doesn't fear Alt+F4 anymore, utterly refusing to return to her room.

Haven't restarted the PC though, (it installed a bunch of python packages, so a restart may be necessary). Also didn't delete old .conf file from ~/.elisa-0.5/.

Any Gives? Please I need her back ASAP, every moment without her is agony](*,)!!!

---

### Post by Ekeluo on 2008-12-28
Awwww, I'm hurting here someone pleeeeeeez help me? Please.

(Restarted PC,no difference at all)

---

### Post by xc3RnbFO8P on 2008-12-28
Intrepid?
I find it best to install it from Synaptic Package Manager,
it is the supported version.

---

### Post by Ekeluo on 2008-12-28
I installed that one first and had the black screen problem. Though a new one (with new pigment) could cure, but no...

---

### Post by xc3RnbFO8P on 2008-12-28
If you start Elisa from Terminal, does it report errors?
Do this:
> sudo gedit /home/your folder/.elisa-0.5/elisa_?.conf
and change this line (so it wont start in fullscreen)
**start_fullscreen = '1'** to **start_fullscreen = '0'**

---

### Post by Ekeluo on 2008-12-28
The terminal output is quite a lot :
```
kels@kels-laptop:~$ elisa -u
Launcher core version: 0.5.22
Current core version: 0.5.22
/usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
<type 'exceptions.ValueError'>
Python 2.5.2: /usr/bin/python
Sun Dec 28 22:14:37 2008

A problem occurred in a Python script.  Here is the sequence of
function calls leading up to the error, in the order they occurred.

 /usr/lib/python2.5/site-packages/elisa/core/media_directory_helper.py in __init__(self=<elisa.core.media_directory_helper.MediaDirectoryHelper object at 0x9a0826c>)
   32                 self.media_dir = self.get_windows_media_directory()
   33             else:
   34                 self.media_dir = self.get_linux_media_directory()
   35         except Exception, e:
   36             # if retrieving default directories fails log the error and go on
self = <elisa.core.media_directory_helper.MediaDirectoryHelper object at 0x9a0826c>
self.media_dir = {}
self.get_linux_media_directory = <bound method MediaDirectoryHelper.get_linux_med...helper.MediaDirectoryHelper object at 0x9a0826c>>

 /usr/lib/python2.5/site-packages/elisa/core/media_directory_helper.py in get_linux_media_directory(self=<elisa.core.media_directory_helper.MediaDirectoryHelper object at 0x9a0826c>)
   52                        'videos': 'video'}
   53         home = os.path.expanduser("~")
   54         for d in xdg.xdg_content():
   55             directory_path = d[0]
   56             if os.path.normpath(directory_path) == home:
d undefined
xdg = <module 'elisa.extern.coherence.xdg' from '/usr/....5/site-packages/elisa/extern/coherence/xdg.pyc'>
xdg.xdg_content = <function xdg_content at 0xa1ce764>

 /usr/lib/python2.5/site-packages/elisa/extern/coherence/xdg.py in xdg_content()
   23             if not line.startswith('#'):
   24                 line = line.strip()
   25                 key,value = line.split('=')
   26                 try:
   27                     info = hot_dirs[key]
key = 'XDG_PICTURES_DIR'
value = '/home/kels/Pictures'
line = ''
line.split = <built-in method split of str object at 0xb7dbd098>
<type 'exceptions.ValueError'>: need more than 1 value to unpack
    __class__ = <type 'exceptions.ValueError'>
    __delattr__ = <method-wrapper '__delattr__' of exceptions.ValueError object at 0xa1d9b8c>
    __dict__ = {}
    __doc__ = 'Inappropriate argument value (of correct type).'
    __getattribute__ = <method-wrapper '__getattribute__' of exceptions.ValueError object at 0xa1d9b8c>
    __getitem__ = <method-wrapper '__getitem__' of exceptions.ValueError object at 0xa1d9b8c>
    __getslice__ = <method-wrapper '__getslice__' of exceptions.ValueError object at 0xa1d9b8c>
    __hash__ = <method-wrapper '__hash__' of exceptions.ValueError object at 0xa1d9b8c>
    __init__ = <method-wrapper '__init__' of exceptions.ValueError object at 0xa1d9b8c>
    __new__ = <built-in method __new__ of type object at 0x8146fe0>
    __reduce__ = <built-in method __reduce__ of exceptions.ValueError object at 0xa1d9b8c>
    __reduce_ex__ = <built-in method __reduce_ex__ of exceptions.ValueError object at 0xa1d9b8c>
    __repr__ = <method-wrapper '__repr__' of exceptions.ValueError object at 0xa1d9b8c>
    __setattr__ = <method-wrapper '__setattr__' of exceptions.ValueError object at 0xa1d9b8c>
    __setstate__ = <built-in method __setstate__ of exceptions.ValueError object at 0xa1d9b8c>
    __str__ = <method-wrapper '__str__' of exceptions.ValueError object at 0xa1d9b8c>
    args = ('need more than 1 value to unpack',)
    message = 'need more than 1 value to unpack'

The above is a description of an error in a Python program.  Here is
the original traceback:

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/elisa/core/media_directory_helper.py", line 34, in __init__
    self.media_dir = self.get_linux_media_directory()
  File "/usr/lib/python2.5/site-packages/elisa/core/media_directory_helper.py", line 54, in get_linux_media_directory
    for d in xdg.xdg_content():
  File "/usr/lib/python2.5/site-packages/elisa/extern/coherence/xdg.py", line 25, in xdg_content
    key,value = line.split('=')
ValueError: need more than 1 value to unpack


WARN  MainThread      application                 Dec 28 22:14:38  Retrieving default media directories failed. Error logged at /tmp/elisa_aK262d.txt (elisa/core/media_directory_helper.py:39)
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 226, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 705, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/task.py", line 251, in _tick
    result = iterator.next()
  File "/usr/lib/python2.5/site-packages/elisa/core/manager.py", line 101, in load_components_iter
    dfr = plugin_registry.create_component(component_name)
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/elisa/core/plugin_registry.py", line 940, in create_component
    component_class = reflect.namedAny('%s.%s' % (module, klass))
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 426, in namedAny
    topLevelPackage = _importAndCheckStack(trialname)
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 377, in _importAndCheckStack
    return __import__(importName)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/yesfm/yesfm_resource.py", line 28, in <module>
    from elisa.plugins.base.models.image import ImageModel
  File "/usr/lib/python2.5/site-packages/elisa/plugins/base/models/image.py", line 45, in <module>
    _ = install_translation('base')
  File "/usr/lib/python2.5/site-packages/elisa/core/utils/i18n.py", line 90, in install_translation
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG

WARN  MainThread      resource_manager            Dec 28 22:14:38  Creating elisa.plugins.yesfm.yesfm_resource:YesfmResource failed. A full traceback can be found at /tmp/elisa_DdkEMa.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 226, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 705, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/task.py", line 251, in _tick
    result = iterator.next()
  File "/usr/lib/python2.5/site-packages/elisa/core/manager.py", line 101, in load_components_iter
    dfr = plugin_registry.create_component(component_name)
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/elisa/core/plugin_registry.py", line 940, in create_component
    component_class = reflect.namedAny('%s.%s' % (module, klass))
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 426, in namedAny
    topLevelPackage = _importAndCheckStack(trialname)
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 377, in _importAndCheckStack
    return __import__(importName)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/database/dbus_service.py", line 37, in <module>
    from elisa.plugins.poblesec.music_library import album_cover_retriever
  File "/usr/lib/python2.5/site-packages/elisa/plugins/poblesec/music_library.py", line 32, in <module>
    from elisa.plugins.poblesec.base.list import GenericListViewMode
  File "/usr/lib/python2.5/site-packages/elisa/plugins/poblesec/base/list.py", line 23, in <module>
    from elisa.plugins.poblesec.actions import Action
  File "/usr/lib/python2.5/site-packages/elisa/plugins/poblesec/actions.py", line 26, in <module>
    from elisa.plugins.base.models.image import ImageModel
  File "/usr/lib/python2.5/site-packages/elisa/plugins/base/models/image.py", line 45, in <module>
    _ = install_translation('base')
  File "/usr/lib/python2.5/site-packages/elisa/core/utils/i18n.py", line 90, in install_translation
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG

WARN  MainThread      service_manager             Dec 28 22:14:39  Creating elisa.plugins.database.dbus_service:DatabaseDBusServiceProvider failed. A full traceback can be found at /tmp/elisa_980BBK.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 226, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 705, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/task.py", line 251, in _tick
    result = iterator.next()
  File "/usr/lib/python2.5/site-packages/elisa/core/manager.py", line 101, in load_components_iter
    dfr = plugin_registry.create_component(component_name)
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/elisa/core/plugin_registry.py", line 940, in create_component
    component_class = reflect.namedAny('%s.%s' % (module, klass))
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 426, in namedAny
    topLevelPackage = _importAndCheckStack(trialname)
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 377, in _importAndCheckStack
    return __import__(importName)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/database/media_scanner.py", line 40, in <module>
    from elisa.plugins.database.database_parser import DatabaseParser
  File "/usr/lib/python2.5/site-packages/elisa/plugins/database/database_parser.py", line 23, in <module>
    from elisa.plugins.database.models import Artist, MusicAlbum, MusicTrack, \
  File "/usr/lib/python2.5/site-packages/elisa/plugins/database/models.py", line 34, in <module>
    _ = install_translation('database')
  File "/usr/lib/python2.5/site-packages/elisa/core/utils/i18n.py", line 90, in install_translation
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG

WARN  MainThread      resource_manager            Dec 28 22:14:39  Creating elisa.plugins.database.media_scanner:MediaScanner failed. A full traceback can be found at /tmp/elisa_N5OaLp.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/elisa/core/launcher.py", line 367, in run_application
    reactor.run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 186, in run
    self.__run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 226, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 705, in runUntilCurrent
    call.func(*call.args, **call.kw)
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/task.py", line 251, in _tick
    result = iterator.next()
  File "/usr/lib/python2.5/site-packages/elisa/plugins/search/search_metaresource_provider.py", line 90, in iterate
    klass = entry.load()
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 1913, in load
    entry = __import__(self.module_name, globals(),globals(), ['__name__'])
  File "/usr/lib/python2.5/site-packages/elisa/plugins/database/searcher.py", line 28, in <module>
    from elisa.plugins.database.models import MusicAlbum, MusicTrack, Artist, File
  File "/usr/lib/python2.5/site-packages/elisa/plugins/database/models.py", line 34, in <module>
    _ = install_translation('database')
  File "/usr/lib/python2.5/site-packages/elisa/core/utils/i18n.py", line 90, in install_translation
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG

WARN  MainThread      resource_manager            Dec 28 22:14:39  Creating elisa.plugins.search.search_metaresource_provider:SearchMetaresourceProvider failed. A full traceback can be found at /tmp/elisa_nlgp8p.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 226, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 705, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/task.py", line 251, in _tick
    result = iterator.next()
  File "/usr/lib/python2.5/site-packages/elisa/core/manager.py", line 101, in load_components_iter
    dfr = plugin_registry.create_component(component_name)
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/elisa/core/plugin_registry.py", line 940, in create_component
    component_class = reflect.namedAny('%s.%s' % (module, klass))
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 426, in namedAny
    topLevelPackage = _importAndCheckStack(trialname)
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 377, in _importAndCheckStack
    return __import__(importName)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/amazon/resource_provider.py", line 33, in <module>
    from elisa.plugins.base.models.image import ImageModel
  File "/usr/lib/python2.5/site-packages/elisa/plugins/base/models/image.py", line 45, in <module>
    _ = install_translation('base')
  File "/usr/lib/python2.5/site-packages/elisa/core/utils/i18n.py", line 90, in install_translation
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG

WARN  MainThread      resource_manager            Dec 28 22:14:39  Creating elisa.plugins.amazon.resource_provider:AmazonResourceProvider failed. A full traceback can be found at /tmp/elisa_DWByx8.txt (elisa/core/manager.py:97)
/usr/lib/python2.5/site-packages/elisa/core/service_manager.py:27: DeprecationWarning: ServiceProvider.start is deprecated.
  warn("ServiceProvider.%s is deprecated." % attr, DeprecationWarning)
Traceback (most recent call last):
Failure: elisa.plugins.lirc.lirc_input.NoMappingsFound: Given InputMap 'streamzap.map' not found

WARN  MainThread      input_manager               Dec 28 22:14:39  Creating elisa.plugins.lirc.lirc_input:LircInput failed. A full traceback can be found at /tmp/elisa_jS2P-O.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 226, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 705, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/task.py", line 251, in _tick
    result = iterator.next()
  File "/usr/lib/python2.5/site-packages/elisa/core/manager.py", line 101, in load_components_iter
    dfr = plugin_registry.create_component(component_name)
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/elisa/core/plugin_registry.py", line 940, in create_component
    component_class = reflect.namedAny('%s.%s' % (module, klass))
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 426, in namedAny
    topLevelPackage = _importAndCheckStack(trialname)
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 377, in _importAndCheckStack
    return __import__(importName)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/flickr/resource_provider.py", line 39, in <module>
    from elisa.plugins.base.models.image import ImageModel
  File "/usr/lib/python2.5/site-packages/elisa/plugins/base/models/image.py", line 45, in <module>
    _ = install_translation('base')
  File "/usr/lib/python2.5/site-packages/elisa/core/utils/i18n.py", line 90, in install_translation
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG

WARN  MainThread      resource_manager            Dec 28 22:14:39  Creating elisa.plugins.flickr.resource_provider:FlickrResourceProvider failed. A full traceback can be found at /tmp/elisa_443_vG.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
Failure: exceptions.RuntimeError: hildon not running

WARN  MainThread      service_manager             Dec 28 22:14:39  Creating elisa.plugins.osso.osso_service:OssoService failed. A full traceback can be found at /tmp/elisa_5jAIzS.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 226, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 705, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/task.py", line 251, in _tick
    result = iterator.next()
  File "/usr/lib/python2.5/site-packages/elisa/core/manager.py", line 101, in load_components_iter
    dfr = plugin_registry.create_component(component_name)
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/elisa/core/plugin_registry.py", line 940, in create_component
    component_class = reflect.namedAny('%s.%s' % (module, klass))
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 426, in namedAny
    topLevelPackage = _importAndCheckStack(trialname)
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 377, in _importAndCheckStack
    return __import__(importName)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/youtube/resource_provider.py", line 33, in <module>
    from elisa.plugins.base.models.image import ImageModel
  File "/usr/lib/python2.5/site-packages/elisa/plugins/base/models/image.py", line 45, in <module>
    _ = install_translation('base')
  File "/usr/lib/python2.5/site-packages/elisa/core/utils/i18n.py", line 90, in install_translation
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG

WARN  MainThread      resource_manager            Dec 28 22:14:39  Creating elisa.plugins.youtube.resource_provider:YoutubeResourceProvider failed. A full traceback can be found at /tmp/elisa_k7Irky.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 226, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 705, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/task.py", line 251, in _tick
    result = iterator.next()
  File "/usr/lib/python2.5/site-packages/elisa/core/manager.py", line 101, in load_components_iter
    dfr = plugin_registry.create_component(component_name)
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/elisa/core/plugin_registry.py", line 940, in create_component
    component_class = reflect.namedAny('%s.%s' % (module, klass))
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 426, in namedAny
    topLevelPackage = _importAndCheckStack(trialname)
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 377, in _importAndCheckStack
    return __import__(importName)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/discogs/discogs_resource.py", line 32, in <module>
    from elisa.plugins.base.models.image import ImageModel
  File "/usr/lib/python2.5/site-packages/elisa/plugins/base/models/image.py", line 45, in <module>
    _ = install_translation('base')
  File "/usr/lib/python2.5/site-packages/elisa/core/utils/i18n.py", line 90, in install_translation
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG

WARN  MainThread      resource_manager            Dec 28 22:14:39  Creating elisa.plugins.discogs.discogs_resource:DiscogsResource failed. A full traceback can be found at /tmp/elisa_jESM64.txt (elisa/core/manager.py:97)
Unhandled error in Deferred:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 226, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 705, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py", line 527, in _load_first_controller
    dfr = self.create_controller(controller_path)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py", line 161, in create_controller
    dfr = plugin_registry.create_component(controller, config, **kwargs)
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/elisa/core/plugin_registry.py", line 940, in create_component
    component_class = reflect.namedAny('%s.%s' % (module, klass))
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 426, in namedAny
    topLevelPackage = _importAndCheckStack(trialname)
  File "/usr/lib/python2.5/site-packages/twisted/python/reflect.py", line 377, in _importAndCheckStack
    return __import__(importName)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/poblesec/main.py", line 26, in <module>
    from elisa.plugins.base.models.image import ImageModel
  File "/usr/lib/python2.5/site-packages/elisa/plugins/base/models/image.py", line 45, in <module>
    _ = install_translation('base')
  File "/usr/lib/python2.5/site-packages/elisa/core/utils/i18n.py", line 90, in install_translation
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG
WARN  MainThread      application                 Dec 28 22:14:49  An Traceback occurred and got saved to /tmp/elisa_CnSEaj.txt (elisa/core/application.py:357)
<type 'exceptions.AttributeError'>
Python 2.5.2: /usr/bin/python
Sun Dec 28 22:14:49 2008

A problem occurred in a Python script.  Here is the sequence of
function calls leading up to the error, in the order they occurred.

 /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py in _viewport_delete_event(self=<elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>, viewport=<__main__.PgmGlViewport object (pgmglviewport0) at 0xa146824>, event=<PgmEvent at 0xaa14600>)
  541 
  542     def _viewport_delete_event(self, viewport, event):
  543         common.application.stop()
  544 
  545     def reduce_window(self):
global common = <module 'elisa.core.common' from '/usr/lib/python2.5/site-packages/elisa/core/common.py'>
common.application = <elisa.core.application.Application object at 0x997994c>
common.application.stop = <bound method Application.stop of <elisa.core.application.Application object at 0x997994c>>

 /usr/lib/python2.5/site-packages/elisa/core/application.py in stop(self=<elisa.core.application.Application object at 0x997994c>, stop_reactor=True)
  553             # managers
  554             self.info("Stopping interface controller")
  555             dfr = self.interface_controller.stop()
  556             dfr.addCallback(interface_controller_stopped)
  557             return dfr
dfr undefined
self = <elisa.core.application.Application object at 0x997994c>
self.interface_controller = <elisa.core.interface_controller.InterfaceController object at 0xa1e6c2c>
self.interface_controller.stop = <bound method InterfaceController.stop of <elisa...troller.InterfaceController object at 0xa1e6c2c>>

 /usr/lib/python2.5/site-packages/elisa/core/interface_controller.py in stop(self=<elisa.core.interface_controller.InterfaceController object at 0xa1e6c2c>)
  139 
  140         for frontend in self.frontends.values():
  141             dfr = frontend.clean()
  142             dfrs.append(dfr)
  143 
dfr undefined
frontend = <elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>
frontend.clean = <bound method PigmentFrontend.clean of <elisa.pl...nt_frontend.PigmentFrontend object at 0xa224a8c>>

 /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py in clean(self=<elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>)
  693         self._clean_dbus()
  694 
  695         if self.controller:
  696              self.controller.removed()
  697 
self = <elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>
self.controller undefined
<type 'exceptions.AttributeError'>: 'PigmentFrontend' object has no attribute 'controller'
    __class__ = <type 'exceptions.AttributeError'>
    __delattr__ = <method-wrapper '__delattr__' of exceptions.AttributeError object at 0xa20f78c>
    __dict__ = {}
    __doc__ = 'Attribute not found.'
    __getattribute__ = <method-wrapper '__getattribute__' of exceptions.AttributeError object at 0xa20f78c>
    __getitem__ = <method-wrapper '__getitem__' of exceptions.AttributeError object at 0xa20f78c>
    __getslice__ = <method-wrapper '__getslice__' of exceptions.AttributeError object at 0xa20f78c>
    __hash__ = <method-wrapper '__hash__' of exceptions.AttributeError object at 0xa20f78c>
    __init__ = <method-wrapper '__init__' of exceptions.AttributeError object at 0xa20f78c>
    __new__ = <built-in method __new__ of type object at 0x8146aa0>
    __reduce__ = <built-in method __reduce__ of exceptions.AttributeError object at 0xa20f78c>
    __reduce_ex__ = <built-in method __reduce_ex__ of exceptions.AttributeError object at 0xa20f78c>
    __repr__ = <method-wrapper '__repr__' of exceptions.AttributeError object at 0xa20f78c>
    __setattr__ = <method-wrapper '__setattr__' of exceptions.AttributeError object at 0xa20f78c>
    __setstate__ = <built-in method __setstate__ of exceptions.AttributeError object at 0xa20f78c>
    __str__ = <method-wrapper '__str__' of exceptions.AttributeError object at 0xa20f78c>
    args = ("'PigmentFrontend' object has no attribute 'controller'",)
    message = "'PigmentFrontend' object has no attribute 'controller'"

The above is a description of an error in a Python program.  Here is
the original traceback:

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py", line 543, in _viewport_delete_event
    common.application.stop()
  File "/usr/lib/python2.5/site-packages/elisa/core/application.py", line 555, in stop
    dfr = self.interface_controller.stop()
  File "/usr/lib/python2.5/site-packages/elisa/core/interface_controller.py", line 141, in stop
    dfr = frontend.clean()
  File "/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py", line 695, in clean
    if self.controller:
AttributeError: 'PigmentFrontend' object has no attribute 'controller'


WARN  MainThread      application                 Dec 28 22:14:49  An Traceback occurred and got saved to /tmp/elisa_OvQC9a.txt (elisa/core/application.py:357)
<type 'exceptions.AttributeError'>
Python 2.5.2: /usr/bin/python
Sun Dec 28 22:14:49 2008

A problem occurred in a Python script.  Here is the sequence of
function calls leading up to the error, in the order they occurred.

 /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py in handle_input(self=<elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>, input_manager=<InputManager object at 0xa1e32fc (elisa+core+input_manager+InputManager at 0xa0a1390)>, input_event=<elisa.core.input_event.InputEvent instance at 0xaa001ec>)
  549     def handle_input(self, input_manager, input_event):
  550         # forward it to the controller
  551         self.controller.handle_input(input_manager, input_event)
  552 
  553     def _initialize_theme(self):
self = <elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>
self.controller undefined
input_manager = <InputManager object at 0xa1e32fc (elisa+core+input_manager+InputManager at 0xa0a1390)>
input_event = <elisa.core.input_event.InputEvent instance at 0xaa001ec>
<type 'exceptions.AttributeError'>: 'PigmentFrontend' object has no attribute 'controller'
    __class__ = <type 'exceptions.AttributeError'>
    __delattr__ = <method-wrapper '__delattr__' of exceptions.AttributeError object at 0xad170ac>
    __dict__ = {}
    __doc__ = 'Attribute not found.'
    __getattribute__ = <method-wrapper '__getattribute__' of exceptions.AttributeError object at 0xad170ac>
    __getitem__ = <method-wrapper '__getitem__' of exceptions.AttributeError object at 0xad170ac>
    __getslice__ = <method-wrapper '__getslice__' of exceptions.AttributeError object at 0xad170ac>
    __hash__ = <method-wrapper '__hash__' of exceptions.AttributeError object at 0xad170ac>
    __init__ = <method-wrapper '__init__' of exceptions.AttributeError object at 0xad170ac>
    __new__ = <built-in method __new__ of type object at 0x8146aa0>
    __reduce__ = <built-in method __reduce__ of exceptions.AttributeError object at 0xad170ac>
    __reduce_ex__ = <built-in method __reduce_ex__ of exceptions.AttributeError object at 0xad170ac>
    __repr__ = <method-wrapper '__repr__' of exceptions.AttributeError object at 0xad170ac>
    __setattr__ = <method-wrapper '__setattr__' of exceptions.AttributeError object at 0xad170ac>
    __setstate__ = <built-in method __setstate__ of exceptions.AttributeError object at 0xad170ac>
    __str__ = <method-wrapper '__str__' of exceptions.AttributeError object at 0xad170ac>
    args = ("'PigmentFrontend' object has no attribute 'controller'",)
    message = "'PigmentFrontend' object has no attribute 'controller'"

The above is a description of an error in a Python program.  Here is
the original traceback:

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py", line 551, in handle_input
    self.controller.handle_input(input_manager, input_event)
AttributeError: 'PigmentFrontend' object has no attribute 'controller'


WARN  MainThread      application                 Dec 28 22:14:52  An Traceback occurred and got saved to /tmp/elisa_BzFJ2c.txt (elisa/core/application.py:357)
<type 'exceptions.AttributeError'>
Python 2.5.2: /usr/bin/python
Sun Dec 28 22:14:52 2008

A problem occurred in a Python script.  Here is the sequence of
function calls leading up to the error, in the order they occurred.

 /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py in _viewport_delete_event(self=<elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>, viewport=<__main__.PgmGlViewport object (pgmglviewport0) at 0xa146824>, event=<PgmEvent at 0xaa14580>)
  541 
  542     def _viewport_delete_event(self, viewport, event):
  543         common.application.stop()
  544 
  545     def reduce_window(self):
global common = <module 'elisa.core.common' from '/usr/lib/python2.5/site-packages/elisa/core/common.py'>
common.application = <elisa.core.application.Application object at 0x997994c>
common.application.stop = <bound method Application.stop of <elisa.core.application.Application object at 0x997994c>>

 /usr/lib/python2.5/site-packages/elisa/core/application.py in stop(self=<elisa.core.application.Application object at 0x997994c>, stop_reactor=True)
  553             # managers
  554             self.info("Stopping interface controller")
  555             dfr = self.interface_controller.stop()
  556             dfr.addCallback(interface_controller_stopped)
  557             return dfr
dfr undefined
self = <elisa.core.application.Application object at 0x997994c>
self.interface_controller = <elisa.core.interface_controller.InterfaceController object at 0xa1e6c2c>
self.interface_controller.stop = <bound method InterfaceController.stop of <elisa...troller.InterfaceController object at 0xa1e6c2c>>

 /usr/lib/python2.5/site-packages/elisa/core/interface_controller.py in stop(self=<elisa.core.interface_controller.InterfaceController object at 0xa1e6c2c>)
  139 
  140         for frontend in self.frontends.values():
  141             dfr = frontend.clean()
  142             dfrs.append(dfr)
  143 
dfr undefined
frontend = <elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>
frontend.clean = <bound method PigmentFrontend.clean of <elisa.pl...nt_frontend.PigmentFrontend object at 0xa224a8c>>

 /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py in clean(self=<elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>)
  691 
  692     def clean(self):
  693         self._clean_dbus()
  694 
  695         if self.controller:
self = <elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>
self._clean_dbus = <bound method PigmentFrontend._clean_dbus of <el...nt_frontend.PigmentFrontend object at 0xa224a8c>>

 /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py in _clean_dbus(self=<elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>)
  760 
  761         bus = dbus.SessionBus()
  762         self.dbus_frontend.remove_from_connection(bus,
  763                 '/com/fluendo/Elisa/Plugins/Pigment/Frontend')
  764         # BusName implements __del__, eew
self = <elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>
self.dbus_frontend undefined
bus = <dbus._dbus.SessionBus (session) at 0x98fc4dc>
<type 'exceptions.AttributeError'>: 'PigmentFrontend' object has no attribute 'dbus_frontend'
    __class__ = <type 'exceptions.AttributeError'>
    __delattr__ = <method-wrapper '__delattr__' of exceptions.AttributeError object at 0xad1778c>
    __dict__ = {}
    __doc__ = 'Attribute not found.'
    __getattribute__ = <method-wrapper '__getattribute__' of exceptions.AttributeError object at 0xad1778c>
    __getitem__ = <method-wrapper '__getitem__' of exceptions.AttributeError object at 0xad1778c>
    __getslice__ = <method-wrapper '__getslice__' of exceptions.AttributeError object at 0xad1778c>
    __hash__ = <method-wrapper '__hash__' of exceptions.AttributeError object at 0xad1778c>
    __init__ = <method-wrapper '__init__' of exceptions.AttributeError object at 0xad1778c>
    __new__ = <built-in method __new__ of type object at 0x8146aa0>
    __reduce__ = <built-in method __reduce__ of exceptions.AttributeError object at 0xad1778c>
    __reduce_ex__ = <built-in method __reduce_ex__ of exceptions.AttributeError object at 0xad1778c>
    __repr__ = <method-wrapper '__repr__' of exceptions.AttributeError object at 0xad1778c>
    __setattr__ = <method-wrapper '__setattr__' of exceptions.AttributeError object at 0xad1778c>
    __setstate__ = <built-in method __setstate__ of exceptions.AttributeError object at 0xad1778c>
    __str__ = <method-wrapper '__str__' of exceptions.AttributeError object at 0xad1778c>
    args = ("'PigmentFrontend' object has no attribute 'dbus_frontend'",)
    message = "'PigmentFrontend' object has no attribute 'dbus_frontend'"

The above is a description of an error in a Python program.  Here is
the original traceback:

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py", line 543, in _viewport_delete_event
    common.application.stop()
  File "/usr/lib/python2.5/site-packages/elisa/core/application.py", line 555, in stop
    dfr = self.interface_controller.stop()
  File "/usr/lib/python2.5/site-packages/elisa/core/interface_controller.py", line 141, in stop
    dfr = frontend.clean()
  File "/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py", line 693, in clean
    self._clean_dbus()
  File "/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py", line 762, in _clean_dbus
    self.dbus_frontend.remove_from_connection(bus,
AttributeError: 'PigmentFrontend' object has no attribute 'dbus_frontend'


WARN  MainThread      application                 Dec 28 22:14:52  An Traceback occurred and got saved to /tmp/elisa_NmZPL_.txt (elisa/core/application.py:357)
<type 'exceptions.AttributeError'>
Python 2.5.2: /usr/bin/python
Sun Dec 28 22:14:52 2008

A problem occurred in a Python script.  Here is the sequence of
function calls leading up to the error, in the order they occurred.

 /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py in handle_input(self=<elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>, input_manager=<InputManager object at 0xa1e32fc (elisa+core+input_manager+InputManager at 0xa0a1390)>, input_event=<elisa.core.input_event.InputEvent instance at 0xad16e0c>)
  549     def handle_input(self, input_manager, input_event):
  550         # forward it to the controller
  551         self.controller.handle_input(input_manager, input_event)
  552 
  553     def _initialize_theme(self):
self = <elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>
self.controller undefined
input_manager = <InputManager object at 0xa1e32fc (elisa+core+input_manager+InputManager at 0xa0a1390)>
input_event = <elisa.core.input_event.InputEvent instance at 0xad16e0c>
<type 'exceptions.AttributeError'>: 'PigmentFrontend' object has no attribute 'controller'
    __class__ = <type 'exceptions.AttributeError'>
    __delattr__ = <method-wrapper '__delattr__' of exceptions.AttributeError object at 0xac57b0c>
    __dict__ = {}
    __doc__ = 'Attribute not found.'
    __getattribute__ = <method-wrapper '__getattribute__' of exceptions.AttributeError object at 0xac57b0c>
    __getitem__ = <method-wrapper '__getitem__' of exceptions.AttributeError object at 0xac57b0c>
    __getslice__ = <method-wrapper '__getslice__' of exceptions.AttributeError object at 0xac57b0c>
    __hash__ = <method-wrapper '__hash__' of exceptions.AttributeError object at 0xac57b0c>
    __init__ = <method-wrapper '__init__' of exceptions.AttributeError object at 0xac57b0c>
    __new__ = <built-in method __new__ of type object at 0x8146aa0>
    __reduce__ = <built-in method __reduce__ of exceptions.AttributeError object at 0xac57b0c>
    __reduce_ex__ = <built-in method __reduce_ex__ of exceptions.AttributeError object at 0xac57b0c>
    __repr__ = <method-wrapper '__repr__' of exceptions.AttributeError object at 0xac57b0c>
    __setattr__ = <method-wrapper '__setattr__' of exceptions.AttributeError object at 0xac57b0c>
    __setstate__ = <built-in method __setstate__ of exceptions.AttributeError object at 0xac57b0c>
    __str__ = <method-wrapper '__str__' of exceptions.AttributeError object at 0xac57b0c>
    args = ("'PigmentFrontend' object has no attribute 'controller'",)
    message = "'PigmentFrontend' object has no attribute 'controller'"

The above is a description of an error in a Python program.  Here is
the original traceback:

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py", line 551, in handle_input
    self.controller.handle_input(input_manager, input_event)
AttributeError: 'PigmentFrontend' object has no attribute 'controller'


WARN  MainThread      application                 Dec 28 22:14:53  An Traceback occurred and got saved to /tmp/elisa_FB5lG6.txt (elisa/core/application.py:357)
<type 'exceptions.AttributeError'>
Python 2.5.2: /usr/bin/python
Sun Dec 28 22:14:52 2008

A problem occurred in a Python script.  Here is the sequence of
function calls leading up to the error, in the order they occurred.

 /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py in _viewport_delete_event(self=<elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>, viewport=<__main__.PgmGlViewport object (pgmglviewport0) at 0xa146824>, event=<PgmEvent at 0xaa14520>)
  541 
  542     def _viewport_delete_event(self, viewport, event):
  543         common.application.stop()
  544 
  545     def reduce_window(self):
global common = <module 'elisa.core.common' from '/usr/lib/python2.5/site-packages/elisa/core/common.py'>
common.application = <elisa.core.application.Application object at 0x997994c>
common.application.stop = <bound method Application.stop of <elisa.core.application.Application object at 0x997994c>>

 /usr/lib/python2.5/site-packages/elisa/core/application.py in stop(self=<elisa.core.application.Application object at 0x997994c>, stop_reactor=True)
  553             # managers
  554             self.info("Stopping interface controller")
  555             dfr = self.interface_controller.stop()
  556             dfr.addCallback(interface_controller_stopped)
  557             return dfr
dfr undefined
self = <elisa.core.application.Application object at 0x997994c>
self.interface_controller = <elisa.core.interface_controller.InterfaceController object at 0xa1e6c2c>
self.interface_controller.stop = <bound method InterfaceController.stop of <elisa...troller.InterfaceController object at 0xa1e6c2c>>

 /usr/lib/python2.5/site-packages/elisa/core/interface_controller.py in stop(self=<elisa.core.interface_controller.InterfaceController object at 0xa1e6c2c>)
  139 
  140         for frontend in self.frontends.values():
  141             dfr = frontend.clean()
  142             dfrs.append(dfr)
  143 
dfr undefined
frontend = <elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>
frontend.clean = <bound method PigmentFrontend.clean of <elisa.pl...nt_frontend.PigmentFrontend object at 0xa224a8c>>

 /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py in clean(self=<elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>)
  691 
  692     def clean(self):
  693         self._clean_dbus()
  694 
  695         if self.controller:
self = <elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>
self._clean_dbus = <bound method PigmentFrontend._clean_dbus of <el...nt_frontend.PigmentFrontend object at 0xa224a8c>>

 /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py in _clean_dbus(self=<elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>)
  760 
  761         bus = dbus.SessionBus()
  762         self.dbus_frontend.remove_from_connection(bus,
  763                 '/com/fluendo/Elisa/Plugins/Pigment/Frontend')
  764         # BusName implements __del__, eew
self = <elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>
self.dbus_frontend undefined
bus = <dbus._dbus.SessionBus (session) at 0x98fc4dc>
<type 'exceptions.AttributeError'>: 'PigmentFrontend' object has no attribute 'dbus_frontend'
    __class__ = <type 'exceptions.AttributeError'>
    __delattr__ = <method-wrapper '__delattr__' of exceptions.AttributeError object at 0xad266cc>
    __dict__ = {}
    __doc__ = 'Attribute not found.'
    __getattribute__ = <method-wrapper '__getattribute__' of exceptions.AttributeError object at 0xad266cc>
    __getitem__ = <method-wrapper '__getitem__' of exceptions.AttributeError object at 0xad266cc>
    __getslice__ = <method-wrapper '__getslice__' of exceptions.AttributeError object at 0xad266cc>
    __hash__ = <method-wrapper '__hash__' of exceptions.AttributeError object at 0xad266cc>
    __init__ = <method-wrapper '__init__' of exceptions.AttributeError object at 0xad266cc>
    __new__ = <built-in method __new__ of type object at 0x8146aa0>
    __reduce__ = <built-in method __reduce__ of exceptions.AttributeError object at 0xad266cc>
    __reduce_ex__ = <built-in method __reduce_ex__ of exceptions.AttributeError object at 0xad266cc>
    __repr__ = <method-wrapper '__repr__' of exceptions.AttributeError object at 0xad266cc>
    __setattr__ = <method-wrapper '__setattr__' of exceptions.AttributeError object at 0xad266cc>
    __setstate__ = <built-in method __setstate__ of exceptions.AttributeError object at 0xad266cc>
    __str__ = <method-wrapper '__str__' of exceptions.AttributeError object at 0xad266cc>
    args = ("'PigmentFrontend' object has no attribute 'dbus_frontend'",)
    message = "'PigmentFrontend' object has no attribute 'dbus_frontend'"

The above is a description of an error in a Python program.  Here is
the original traceback:

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py", line 543, in _viewport_delete_event
    common.application.stop()
  File "/usr/lib/python2.5/site-packages/elisa/core/application.py", line 555, in stop
    dfr = self.interface_controller.stop()
  File "/usr/lib/python2.5/site-packages/elisa/core/interface_controller.py", line 141, in stop
    dfr = frontend.clean()
  File "/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py", line 693, in clean
    self._clean_dbus()
  File "/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py", line 762, in _clean_dbus
    self.dbus_frontend.remove_from_connection(bus,
AttributeError: 'PigmentFrontend' object has no attribute 'dbus_frontend'


WARN  MainThread      application                 Dec 28 22:14:53  An Traceback occurred and got saved to /tmp/elisa_6OSn_K.txt (elisa/core/application.py:357)
<type 'exceptions.AttributeError'>
Python 2.5.2: /usr/bin/python
Sun Dec 28 22:14:53 2008

A problem occurred in a Python script.  Here is the sequence of
function calls leading up to the error, in the order they occurred.

 /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py in handle_input(self=<elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>, input_manager=<InputManager object at 0xa1e32fc (elisa+core+input_manager+InputManager at 0xa0a1390)>, input_event=<elisa.core.input_event.InputEvent instance at 0xad16dcc>)
  549     def handle_input(self, input_manager, input_event):
  550         # forward it to the controller
  551         self.controller.handle_input(input_manager, input_event)
  552 
  553     def _initialize_theme(self):
self = <elisa.plugins.pigment.pigment_frontend.PigmentFrontend object at 0xa224a8c>
self.controller undefined
input_manager = <InputManager object at 0xa1e32fc (elisa+core+input_manager+InputManager at 0xa0a1390)>
input_event = <elisa.core.input_event.InputEvent instance at 0xad16dcc>
<type 'exceptions.AttributeError'>: 'PigmentFrontend' object has no attribute 'controller'
    __class__ = <type 'exceptions.AttributeError'>
    __delattr__ = <method-wrapper '__delattr__' of exceptions.AttributeError object at 0xad16e0c>
    __dict__ = {}
    __doc__ = 'Attribute not found.'
    __getattribute__ = <method-wrapper '__getattribute__' of exceptions.AttributeError object at 0xad16e0c>
    __getitem__ = <method-wrapper '__getitem__' of exceptions.AttributeError object at 0xad16e0c>
    __getslice__ = <method-wrapper '__getslice__' of exceptions.AttributeError object at 0xad16e0c>
    __hash__ = <method-wrapper '__hash__' of exceptions.AttributeError object at 0xad16e0c>
    __init__ = <method-wrapper '__init__' of exceptions.AttributeError object at 0xad16e0c>
    __new__ = <built-in method __new__ of type object at 0x8146aa0>
    __reduce__ = <built-in method __reduce__ of exceptions.AttributeError object at 0xad16e0c>
    __reduce_ex__ = <built-in method __reduce_ex__ of exceptions.AttributeError object at 0xad16e0c>
    __repr__ = <method-wrapper '__repr__' of exceptions.AttributeError object at 0xad16e0c>
    __setattr__ = <method-wrapper '__setattr__' of exceptions.AttributeError object at 0xad16e0c>
    __setstate__ = <built-in method __setstate__ of exceptions.AttributeError object at 0xad16e0c>
    __str__ = <method-wrapper '__str__' of exceptions.AttributeError object at 0xad16e0c>
    args = ("'PigmentFrontend' object has no attribute 'controller'",)
    message = "'PigmentFrontend' object has no attribute 'controller'"

The above is a description of an error in a Python program.  Here is
the original traceback:

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py", line 551, in handle_input
    self.controller.handle_input(input_manager, input_event)
AttributeError: 'PigmentFrontend' object has no attribute 'controller'


elisa: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

```

Probably should go to the dev team 4 elisa....

---

### Post by Ashrael on 2009-01-04
Using intrepid 2.6.27-11-generic
... I have installed Elisa three days ago, and had some probls with it, but I managed to solve quite a few in the mean time, I'll try to convey..
The version that is in intrepid repos was full of woe, so I added this repo: [http://ppa.launchpad.net/elisa-developers/ubuntu](http://ppa.launchpad.net/elisa-developers/ubuntu), you have to specify your release, eg. hardy or intrepid.

then in terminal: sudo apt-get purge elisa
then: sudo apt-get autoclean
then open up synaptic.
Somehow it is needed to instal it in two goes, so install python-elisa first (0.5.22), then install elisa and all it says it needs.

This solved the internet issues i had, I still have some warnings but those are mostly logical (hildon, lirc, flickr all of which I do not use), there are some more warnings, but I have not figured out if they are important for me...

HTH, I will keep y'all posted...

---

### Post by Ashrael on 2009-01-04
Oh forgot to post terminal output...

> ~$ elisa
Launcher core version: 0.5.22
Current core version: 0.5.22
/usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
/usr/lib/python2.5/site-packages/elisa/core/service_manager.py:27: DeprecationWarning: ServiceProvider.start is deprecated.
  warn("ServiceProvider.%s is deprecated." % attr, DeprecationWarning)
WARN  MainThread      gst_metadata_slave_process_protocol Jan 04 16:18:47  Starting Slave-2 on unix:/tmp/elisa-metadata-WFazHe.socket launching elisa.plugins.gstreamer.amp_slave.run_slave
(Slave-2 stdout) (elisa/plugins/amp/master.py:54)
Traceback (most recent call last):
Failure: elisa.plugins.lirc.lirc_input.NoMappingsFound: Given InputMap 'streamzap.map' not found

WARN  MainThread      input_manager               Jan 04 16:18:48  Creating elisa.plugins.lirc.lirc_input:LircInput failed. A full traceback can be found at /tmp/elisa_kEu32h.txt (elisa/core/manager.py:97)
WARN  MainThread      gst_metadata_slave_process_protocol Jan 04 16:18:49  /usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
(Slave-2 stderr) (elisa/plugins/amp/master.py:57)
Traceback (most recent call last):
Failure: exceptions.RuntimeError: hildon not running

WARN  MainThread      service_manager             Jan 04 16:18:49  Creating elisa.plugins.osso.osso_service:OssoService failed. A full traceback can be found at /tmp/elisa_bJyz2R.txt (elisa/core/manager.py:97)
WARN  MainThread      gst_metadata_slave_process_protocol Jan 04 16:18:53  Starting Slave-6 on unix:/tmp/elisa-metadata-h0H6uN.socket launching elisa.plugins.gstreamer.amp_slave.run_slave
(Slave-6 stdout) (elisa/plugins/amp/master.py:54)
WARN  MainThread      gst_metadata_slave_process_protocol Jan 04 16:18:54  /usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
(Slave-6 stderr) (elisa/plugins/amp/master.py:57)
==> at [https://login.yahoo.com/config/login?.src=flickr&.pc=5134&.scrumb=0&.pd=c%3DE0.GahOp2e4MjkX.5l2HgAoLkpmyPvccpVM-&.intl=us&.done=https%3A%2F%2Flogin.yahoo.com%2Fconfig%2Fvalidate%3F.src%3Dflickr%26.pc%3D5134%26.scrumb%3D0%26.pd%3Dc%253DE0.GahOp2e4MjkX.5l2HgAoLkpmyPvccpVM-%26.intl%3Dus%26.done%3Dhttp%253A%252F%252Fwww.flickr.com%252Fsignin%252Fyahoo%252F%253Fredir%253D%25252Fservices%25252Fauth%25252F%25253Fperms%25253Ddelete%252526api_key%25253Def2cc311ac8916c794b436bf482c5de5%252526frob%25253D72157612152979010-a7aa8e58c0453715-155096%252526api_sig%25253Dbc32fa65a932b1d5f95d61bd33211eb2](https://login.yahoo.com/config/login?.src=flickr&.pc=5134&.scrumb=0&.pd=c%3DE0.GahOp2e4MjkX.5l2HgAoLkpmyPvccpVM-&.intl=us&.done=https%3A%2F%2Flogin.yahoo.com%2Fconfig%2Fvalidate%3F.src%3Dflickr%26.pc%3D5134%26.scrumb%3D0%26.pd%3Dc%253DE0.GahOp2e4MjkX.5l2HgAoLkpmyPvccpVM-%26.intl%3Dus%26.done%3Dhttp%253A%252F%252Fwww.flickr.com%252Fsignin%252Fyahoo%252F%253Fredir%253D%25252Fservices%25252Fauth%25252F%25253Fperms%25253Ddelete%252526api_key%25253Def2cc311ac8916c794b436bf482c5de5%252526frob%25253D72157612152979010-a7aa8e58c0453715-155096%252526api_sig%25253Dbc32fa65a932b1d5f95d61bd33211eb2)
Note: submit is using submit button: name=".save", value="Sign In"
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 614, in gotResult
    _deferGenerator(g, deferred)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 591, in _deferGenerator
    deferred.callback(result)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 243, in callback
    self._startRunCallbacks(result)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 312, in _startRunCallbacks
    self._runCallbacks()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 328, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/flickr/resource_provider.py", line 269, in response_read
    raise ValueError('%s: %s' %(err_code, err_msg))
exceptions.ValueError: 108: Invalid frob

WARN  MainThread      flickr_resource_provider    Jan 04 16:18:56  Login to Flickr failed. Full output at /tmp/elisa_a5EMf-.txt (elisa/plugins/flickr/resource_provider.py:90)


I hope someone can tell me what interesting functions could still be made to work..
Also I would like to see some sort of browsercapability in elisa, it would be fun to chat and browse the net too from my lazy chair... I :popcorn::guitar::lolflag:

or am I the only lazy sob out there?

---

### Post by Ekeluo on 2009-01-23
Someone pleeeeez help?:sad: Pretty please??:cry:

---

### Post by Ashrael on 2009-01-27
>>> Ekeluo: Have you tried as I suggested above? Have you tried to run elisa as sudo? If that changes anything most likely you have a rights issue somewhere.. And also make sure that you have the right pigment version installed, as the output you gave suggests that this might be the problem. 

HTH!

---

### Post by Ekeluo on 2009-01-28
Output: 
kels@kels-laptop:~/Downloads/Skins, Themes & Icons/Aurora/aurora-1.5$ sudo elisa[sudo] password for kels: 
Launcher core version: 0.5.25
Current core version: 0.5.25
/usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
Traceback (most recent call last):
  File "/usr/bin/elisa", line 8, in <module>
    load_entry_point('elisa==0.5.25', 'gui_scripts', 'elisa')()
  File "/usr/lib/python2.5/site-packages/elisa/core/launcher.py", line 379, in main
    Launcher().main(sys.argv)
  File "/usr/lib/python2.5/site-packages/elisa/core/launcher.py", line 78, in main
    return self.main_after_voodoo(argv)
  File "/usr/lib/python2.5/site-packages/elisa/core/launcher.py", line 217, in main_after_voodoo
    self.run_application()
  File "/usr/lib/python2.5/site-packages/elisa/core/launcher.py", line 346, in run_application
    from elisa.core.application import Application
  File "/usr/lib/python2.5/site-packages/elisa/core/application.py", line 61, in <module>
    from elisa.core.utils.update_checker import UpdateChecker
  File "/usr/lib/python2.5/site-packages/elisa/core/utils/update_checker.py", line 35, in <module>
    from elisa.plugins.base.models.plugin import PluginModel
  File "/usr/lib/python2.5/site-packages/elisa/plugins/base/models/plugin.py", line 25, in <module>
    from elisa.plugins.base.models.image import ImageModel
  File "/usr/lib/python2.5/site-packages/elisa/plugins/base/models/image.py", line 45, in <module>
    _ = install_translation('base')
  File "/usr/lib/python2.5/site-packages/elisa/core/utils/i18n.py", line 90, in install_translation
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: en_NG
kels@kels-laptop:~/Downloads/Skins, Themes & Icons/Aurora/aurora-1.5$

---

### Post by Ekeluo on 2009-07-17
Solved by changing system language from en_NG to en_US.

---

