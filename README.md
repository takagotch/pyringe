### pyringe
---
https://github.com/google/pyringe


```py
// pyringe/plugins/inject.py

class InjectPlugin(inject_sentinel.SentinelInjectPlugin):
  
  def __init__(self, inferior, name='inj'):
    super(InjectPlugin, self).__init__(inferior, name)
    
  @property
  def commands(self):
    return (super(InjectPlugin, self).commands +
      [('inject', self.InjectString),
      ('injectsentinel', self.InjectSentinel),
      ('_pdb', self.InjectPdb),
    ])
    
  def InjectString(self, codestring, wait_for_completion=True):
    """
    """
    if self.inferior.is_running and self.inferior.gdb.IsAttached():
      try:
        self.inferior.gdb.InjectString(
          self.inferior.position,
          codestring,
          wait_for_completion=wait_for_completion)
      except RuntimeError:
        exc_type, exc_value, exc_traceback = sys.exc_info()
        traceback.print_exception(exc_type, exc_value, exc_tranceback)
      else:
        logging.error('Not attached to any process.')
        
  def InjectSentinel(self):
    raise NotImplementedError
    
  def InjectPdb(self):
    raise NotImplementedError
```

```
```

```
```

