Based on
--------

* [DWM 6.0](http://dwm.suckless.org/)
* [Dmenu 4.5](http://tools.suckless.org/dmenu/)
* [Systray patch](http://dwm.suckless.org/patches/systray)
* Xft patch : for [dwm](http://dwm.suckless.org/patches/xft) and [dmenu](http://tools.suckless.org/dmenu/patches/xft)
* [wmname 0.1](http://tools.suckless.org/wmname)
* [slock 1.1](http://tools.suckless.org/slock/)

Default configuration
---------------------

* Prefix path = /usr (need root access to install)
* Preinstalled patches : systray and xft
* Font "Sans" size 12
* Command key mapped on Windows key
  * win + e : open x-file-manager (see below how to set alternatives) 
  * win + s : lock screen (type user password to unlock)
  * win + h : reduce main area
  * win + l : enlarge main area
  * win + m : monocle area
  * win + t : tiled area
  * win + shift + enter : open terminal
  * win + enter         : swap window in main area
  * win + TAB           : focus next area
  * win + shift + TAB   : focus previous area
  * win + shit + c      : close window

Make and install
----------------

```sh
        make
        sudo make install
```

Linux user : if you got a fatal error on "/usr/include/ft2build.h", not finding "freetype/config/ftheader.h" then do the symbolic link below :

```sh
        sudo ln -s /usr/include/freetype2/freetype/ /usr/include/
```

A .xinitrc (or .xprofile) sample is present in [my dotfiles repo](https://github.com/hamdouni/dotfiles) with custom info bar and laptop config. 
The dwm-loop is a shell script containing :

```sh
	#!/bin/sh
	while true; do
	    # Log stderror to a file 
	    dwm 2> ~/.dwm.log
	done
```

How to install new alternative "x-file-manager" ?
---------------------------------------------------

For example, to install thunar as an alternative for x-file-manager, do the below command :

```sh
        # For thunar
        sudo update-alternatives --install /usr/bin/x-file-manager x-file-manager /usr/bin/thunar 1000
        
        # For nautilus (install alternative and prevent nautilus to open desktop) 
        sudo update-alternatives --install /usr/bin/x-file-manager x-file-manager /usr/bin/nautilus 1000
        gsettings set org.gnome.desktop.background show-desktop-icons false
```

How to set the same font in DWM/Xft and in GTK apps ?
------------------------------------------------------------

For example, if we want the 'Ubuntu Mono' font at size 12 :

```sh
        gsettings set org.gnome.desktop.interface monospace-font-name 'Ubuntu Mono 12'
```
