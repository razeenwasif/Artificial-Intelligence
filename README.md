# Artificial Intelligence Projects

This repository collects a set of small game environments paired with AI agents that learn or reason about how to play them. Each subdirectory is a self-contained project that can be run independently and focuses on a different algorithmic approach ranging from heuristic search to evolutionary strategies and deep reinforcement learning.

## Repository Map

| Project | Focus | Primary Entry Points |
| --- | --- | --- |
| `flappybird/` | NEAT-powered agent that learns to fly through pipes by evolving neural network topologies. | `flappybird.py`, `train.py` |
| `snake/` | Deep Q-Network agent assisted by optional A* pathfinding for classic Snake. | `game.py`, `train.py` |
| `pingpong/` | Competitive Pong agents evolved with NEAT that can play against each other or a human. | `main.py` |
| `tictactoe/` | Deterministic Tic-Tac-Toe opponent using minimax with optional random play. | `main.py` |

Each project folder may include additional documentation (for example, `flappybird/README.md` and `snake/README.md`) with deeper dives into controls, configuration, and implementation details.

## Getting Started

- **Python:** Install Python 3.8+ and ensure `pip` is available.
- **Virtual environment (recommended):**
  ```bash
  python -m venv .venv
  source .venv/bin/activate  # Windows: .venv\Scripts\activate
  ```
- **Dependencies:** Install project-specific requirements from within the respective folder. These projects rely on packages such as `pygame`, `neat-python`, `torch`, `gym`, and `numpy`. Use the commands in each subproject’s README or `pip install -r requirements.txt` if provided.

## Running the Projects

### Flappy Bird (NEAT)
- Play the game with an existing trained genome:
  ```bash
  cd flappybird
  python flappybird.py
  ```
- Train a new agent:
  ```bash
  python train.py
  ```
  The training script evolves neural networks and saves the best performer to `bestgenome.pickle`, which the game loads on startup.

### Snake (DQN + A*)
- Manual or AI-driven play:
  ```bash
  cd snake
  python game.py           # manual controls
  python game.py ai        # enable the trained agent
  ```
- Train the Deep Q-Network (requires PyTorch):
  ```bash
  python train.py
  ```
  Training checkpoints and the final model are saved as `dqn_final_model.pth`.

### Ping Pong (NEAT)
- Evaluate an evolved paddle controller against itself or a human:
  ```bash
  cd pingpong
  python main.py
  ```
- Uncomment `run_neat(config)` in `main.py` if you want to retrain and generate a new `bestgenome.pickle`. Training outputs checkpoints under `pingpong/checkpoints/`.

### Tic-Tac-Toe (Minimax)
- Launch the minimax-based opponent:
  ```bash
  cd tictactoe
  python main.py
  ```
- The AI difficulty is configurable in `AI.py` (`level=0` for random moves, `level=1` for minimax).

## Tips & Further Reading

- Look for comments in `config.txt` files (where present) to tweak NEAT hyperparameters.
- The `snake/README.md` and `flappybird/README.md` contain additional context about model architectures, controls, and future improvement ideas; use them as a starting point when modifying or extending the agents.
- For development, consider adding unit tests or visualization hooks to observe agent behavior over time—this is especially helpful when experimenting with new reward functions or heuristics.

Enjoy exploring and extending these AI gameplay experiments! If you add new environments or learning strategies, keep the structure consistent so future contributors can jump in quickly.
