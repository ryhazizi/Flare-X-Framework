# Flare-X Framework 

Very simple and useful PHP framework.

```
<?php

# Turn on the buffer and session!
ob_start();
session_start();

# Load the Flare-X Autoloader
require_once 'flarex/autoload.php';

class App extends \flarex\autoload {
  public function runneable()
  {

    # Initialize Root Path
    $this->init(__DIR__);

    # Import Router Package
    $this->import('router');

    # Intialize Registered Route
    $this->router->init_registered_route();

    # Example Page | localhost/flarex-framework/example
    # Controller name: Testing
    # Function name: test
    $this->router->register()->prefix('example')->add('example', 'testing', 'test');

    # Example Page with parameter | localhost/flarex-framework/example2/{param}
    # Controller name: Testing
    # Function name: test1
    $this->router->register()->prefix('example')->add('example2/{param}', 'testing', 'test1');

    # Example Page with optional parameter | localhost/flarex-framework/example3/{@param}
    # Controller name: Testing
    # Function name: test2
    $this->router->register()->prefix('example')->add('example3/{@param}', 'testing', 'test2');

    # Group Route
    $this->router->register()->group('other', function($r) {

      # Subother Page | localhost/flarex-framework/other/sub
      # Controller name: Other
      # Function name: sub
      $r->prefix('sub')->write_route('subother', 'other', 'sub');
    });

    # Execute Router
    $this->router->execute();

  }
}

# Initialize App
$app = new App;

# Run the App!
$app->runneable();

?>
```
