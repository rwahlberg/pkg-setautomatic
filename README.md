# pkg-setautomatic
Quickly mark multiple manually installed FreeBSD packages as automatic, allowing them to be cleaned up by _autoremove_.

The _autoremove_ command in _pkg_, the FreeBSD package management tool, allows you to quickly remove any packages that were once installed as dependencies but which are not needed anymore. However, packages that were manually installed will never be removed by _autoremove_.

You can use the _query_ command to view a list of packages that have been manually installed:
`pkg query -e "%a=0" %n`

Sometimes you find that you have accumulated a lot of packages that you once installed manually, but which you no longer need. You can _delete_ these packages manually one by one, making sure that other packages don't depend on them (_pkg_ will check this when deleting a package).

This script provides a different approach for quickly removing unused packages. When run, it presents a dialog with a list of manually installed packages, allowing you to select which packages should be marked as automatic. After closing the dialog and confirming your choice, the packages will all be marked as automatic. You can then run `pkg autoremove` to remove any packages that are not needed anymore.

![Screenshot](/images/screenshot.png)
