---
title: "Unity install error"
date: 2010-12-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by weasteam on 2010-12-26
I was trying to install a new version of Unity according to "https://wiki.ubuntu.com/Unity/InstallationGuideFromSource", everything goes well until the "make" for unity:

```
/home/**/Downloads/unity/src/LauncherController.cpp: In member function ‘LauncherIcon* LauncherController::CreateFavorite(const char*)’:
/home/**/Downloads/unity/src/LauncherController.cpp:268: error: ‘bamf_matcher_get_application_for_desktop_file’ was not declared in this scope
/home/**/Downloads/unity/src/LauncherController.cpp:274: error: ‘bamf_view_set_sticky’ was not declared in this scope
/home/**/Downloads/unity/src/LauncherController.cpp:280: error: ‘bamf_view_set_sticky’ was not declared in this scope
make[2]: *** [CMakeFiles/unityshell.dir/src/LauncherController.cpp.o] Error 1
make[1]: *** [CMakeFiles/unityshell.dir/all] Error 2
make: *** [all] Error 2
```

any idea to shot the problem?

---

