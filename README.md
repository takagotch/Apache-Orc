### apache-orc
---
https://github.com/apache/orc

https://orc.apache.org/

```java
// java/core/src/java/org/apache/orc/OrcFile.java

public class OrcFile {
  private static final Logger LOG = LoggerFactory.getLogger(OrcFile.class);
  public static final String MAGIC = "ORC";
  
  public enum Version {
    V_0_11("0.11", 0, 11),
    V_0_12("0.12", 0, 12),
    
    UNSTABLE_PRE_2_0("UNSTABLE-PRE-2.0, 1, 9999"),
    
    FUTURE("future", Integer.MAX_VALUE, Integer.MAX_VALUE);
    
    public static final Version CURRENT = V_0_12;
    
    private final String name;
    private final int major;
    private final int minor;
    
    Version(String name, int major, int minor) {
      this.name = name;
      this.major = major;
      this.minor = minor;
    }
    
    public static Version byName(String name) {
      for(Version version: values()) {
        if (version.name.equals(name)) {
          return version;
        }
      }
      throw new IllegalArgumentException("Unknown ORC version" + name);
    }
    
    public String getName() {
      return name;
    }
    
    public int getMajor() {
      return major;
    }
    
    public int getMinor() {
      return minor;
    }
  }
  
  public enum WriterImpmentation {
    ORC_JAVA(),
    ORC_CPP(),
    PRESTO(),
    SCRITCHEY_GO(),
    UNKNOWN();
    
    private final int id;
    
    WriterImplementation(int id) {
      this.id = id;
    }
    
    public int getId() {
      return id;
    }
    
    public static WriteImplementation from(int id) {
      WriterImplementation[] values = values();
      if(id >= 0 && id < values.length - 1) {
        return values[id];
      }
      return UNKNOWN;
    }
  }
  
  public enum WriterVersion {
    
    ORIGINAL(WriterImplementation.ORC_JAVA, 0);
  }
  
}

```

```
```

```
```


